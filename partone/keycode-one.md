# 关键代码开发
## 创建人脸分析器,检测到微笑后进行拍照
检测后拍照：

 1. 进行分析器参数配置
 2. 把分析器参数配置传给分析器
 3. 在analyzer.setTransacto内通过重写transactResult处理人脸识别后的内容，人脸识别后会返回一个微笑的置信度（简单可以理解为是微笑的概率），只要设置大于一定置信度进行拍照就可以了。
```java
private MLFaceAnalyzer analyzer;private void createFaceAnalyzer() {
    MLFaceAnalyzerSetting setting =
            new MLFaceAnalyzerSetting.Factory()
                    .setFeatureType(MLFaceAnalyzerSetting.TYPE_FEATURES)
                    .setKeyPointType(MLFaceAnalyzerSetting.TYPE_UNSUPPORT_KEYPOINTS)
                    .setMinFaceProportion(0.1f)
                    .setTracingAllowed(true)
                    .create();                 
    this.analyzer = MLAnalyzerFactory.getInstance().getFaceAnalyzer(setting);
    this.analyzer.setTransactor(new MLAnalyzer.MLTransactor<MLFace>() {
        @Override        public void destroy() {
        }

        @Override        public void transactResult(MLAnalyzer.Result<MLFace> result) {
            SparseArray<MLFace> faceSparseArray = result.getAnalyseList();
            int flag = 0;
            for (int i = 0; i < faceSparseArray.size(); i++) {
                MLFaceEmotion emotion = faceSparseArray.valueAt(i).getEmotions();
                if (emotion.getSmilingProbability() > smilingPossibility) {
                    flag++;
                }
            }
            if (flag > faceSparseArray.size() * smilingRate && safeToTakePicture) {
                safeToTakePicture = false;
                mHandler.sendEmptyMessage(TAKE_PHOTO);
            }
        }
    });}
```

拍照存储部分：
```java
private void takePhoto() {
    this.mLensEngine.photograph(null,
            new LensEngine.PhotographListener() {
                @Override                public void takenPhotograph(byte[] bytes) {
                    mHandler.sendEmptyMessage(STOP_PREVIEW);
                    Bitmap bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.length);
                    saveBitmapToDisk(bitmap);
                }
            });}
```

## 创建视觉引擎，捕捉相机动态视频流后传给分析器
```java
private void createLensEngine() {
    Context context = this.getApplicationContext();
    // Create LensEngine
    this.mLensEngine = new LensEngine.Creator(context, this.analyzer).setLensType(this.lensType)
            .applyDisplayDimension(640, 480)
            .applyFps(25.0f)
            .enableAutomaticFocus(true)
            .create();}
```

## 动态权限申请，挂接分析器和视觉引擎创建代码
```java
@Overridepublic void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    this.setContentView(R.layout.activity_live_face_analyse);
    if (savedInstanceState != null) {
        this.lensType = savedInstanceState.getInt("lensType");
    }
    this.mPreview = this.findViewById(R.id.preview);
    this.createFaceAnalyzer();
    this.findViewById(R.id.facingSwitch).setOnClickListener(this);
    // Checking Camera Permissions
    if (ActivityCompat.checkSelfPermission(this, Manifest.permission.CAMERA) == PackageManager.PERMISSION_GRANTED) {
        this.createLensEngine();
    } else {
        this.requestCameraPermission();
    }}
    private void requestCameraPermission() {
    final String[] permissions = new String[]{Manifest.permission.CAMERA, Manifest.permission.WRITE_EXTERNAL_STORAGE};

    if (!ActivityCompat.shouldShowRequestPermissionRationale(this, Manifest.permission.CAMERA)) {
        ActivityCompat.requestPermissions(this, permissions, LiveFaceAnalyseActivity.CAMERA_PERMISSION_CODE);
        return;
    }}@Overridepublic void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions,
                                       @NonNull int[] grantResults) {
    if (requestCode != LiveFaceAnalyseActivity.CAMERA_PERMISSION_CODE) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);
        return;
    }
    if (grantResults.length != 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
        this.createLensEngine();
        return;
    }}
```
