# ImagePicker
<p align="center">
<img src="https://docs.google.com/uc?id=167VvcIE518-bZtOyttFl4vaNWY7gAQS9" height="649" width="300">
</p>

### Dependencies
```dart
dependencies:
  flutter:
    sdk: flutter
  image_picker: ^0.6.2+1
```

```dart
class _MyHomePageState extends State<MyHomePage> {
  File _image;

  Future _getImageFromCamera() async {
    var image = await ImagePicker.pickImage(source: ImageSource.camera);

    setState(() {
      _image = image;
    });
  }

  Future _getImageFromGallery() async {
    var image = await ImagePicker.pickImage(source: ImageSource.gallery);

    setState(() {
      _image = image;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Material(
      child: Column(
        children: <Widget>[
          Expanded(
            child: Container(
              padding: EdgeInsets.only(top: 50),
              child: Center(
                child: Padding(
                  padding: const EdgeInsets.all(20),
                  child: _image == null
                      ? Text(
                          "Pick an image",
                          textAlign: TextAlign.center,
                          style: TextStyle(fontSize: 30),
                        )
                      : Image.file(_image),
                ),
              ),
            ),
          ),
          Padding(
            padding: const EdgeInsets.only(bottom: 30),
            child: Row(
              children: <Widget>[
                Expanded(
                  child: InkWell(
                    onTap: _getImageFromCamera,
                    child: Icon(
                      Icons.camera_alt,
                      size: 100,
                    ),
                  ),
                ),
                Expanded(
                  child: InkWell(
                    onTap: _getImageFromGallery,
                    child: Icon(
                      Icons.image,
                      size: 100,
                    ),
                  ),
                ),
              ],
            ),
          )
        ],
      ),
    );
  }
}
```
