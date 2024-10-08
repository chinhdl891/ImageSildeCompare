### Image Compare Documentation

#### Demo
![Demo](https://github.com/chinhdl891/Image-Compare/blob/master/Screen_recording_20240901_010645-ezgif.com-video-to-gif-converter.gif)

#### Dependency
[![](https://jitpack.io/v/chinhdl891/Image-Compare.svg)](https://jitpack.io/#chinhdl891/Image-Compare)

To include the `Image Compare` in your project, first add the JitPack repository to your `build.gradle` file:

```groovy
allprojects {
    repositories {
        mavenCentral()
        maven { url "https://jitpack.io" }
    }
}
```

Then, add the following dependency:

```groovy
implementation("com.github.chinhdl891:Image-Compare:version")
```

Replace `version` with the latest version available on JitPack.

#### Class Overview
The `Image Compare` class is a custom `ConstraintLayout` used for comparing two images by sliding a divider across the images. It supports various image formats and offers customization through attributes.

#### Attributes
- `background_image`: An image resource ID for the background image.
- `foreground_image`: An image resource ID for the foreground image.
- `slider_icon`: An image resource ID for the slider icon.
- `slider_image_position_percent`: A float value representing the initial position of the slider as a percentage of the view width.

#### Methods

- `setUpSlideCompare(backgroundData: Any)`: 
  - **Description**: Sets up the comparison view with a background image. This method resizes the background image to fit the screen width and creates a transparent foreground image of the same dimensions.
  - **Parameters**: 
    - `backgroundData`: The data representing the background image. It can be a `Bitmap`, `Drawable`, `String` (URL), or `Int` (resource ID).

- `resizeBitmapToFitScreenWidth(bitmap: Bitmap): Bitmap`: 
  - **Description**: Resizes a `Bitmap` to fit the screen width while maintaining the aspect ratio.
  - **Parameters**: 
    - `bitmap`: The bitmap to resize.
  - **Returns**: A resized `Bitmap`.

- `createTransparentBitmap(width: Int, height: Int): Bitmap`: 
  - **Description**: Creates a transparent `Bitmap` with specified width and height.
  - **Parameters**: 
    - `width`: The width of the bitmap.
    - `height`: The height of the bitmap.
  - **Returns**: A transparent `Bitmap`.

- `setForegroundImage(foregroundData: Any)`: 
  - **Description**: Sets the foreground image using the provided data.
  - **Parameters**: 
    - `foregroundData`: The data representing the foreground image. It can be a `Bitmap`, `Drawable`, `String` (URL), or `Int` (resource ID).

- `setHiddenForeground()`: 
  - **Description**: Hides the foreground image and slider, displaying only the background image.

- `setHiddenBackGround()`: 
  - **Description**: Hides the background image and slider, displaying only the foreground image.

- `setPositionSlideImage(percent: Float)`: 
  - **Description**: Sets the slider's position as a percentage of the view width.
  - **Parameters**: 
    - `percent`: A float value between 0 and 1 representing the position of the slider.

- `setImageWidth(progress: Int)`: 
  - **Description**: Adjusts the width of the foreground image according to the slider's position.
  - **Parameters**: 
    - `progress`: The width to set the foreground image to.

### Utility Functions Documentation (Util.kt)

#### Function Overview
Utility functions are helper methods that perform specific tasks like resizing and loading images into an `ImageView`.

#### Functions

- `resizeBitmapToFitScreenWidth(bitmap: Bitmap): Bitmap`:
  - **Description**: Resizes a `Bitmap` to fit the screen width while maintaining the aspect ratio.
  - **Parameters**: 
    - `bitmap`: The bitmap to resize.
  - **Returns**: A resized `Bitmap`.

- `createTransparentBitmap(width: Int, height: Int): Bitmap`: 
  - **Description**: Creates a transparent `Bitmap` with specified width and height.
  - **Parameters**: 
    - `width`: The width of the bitmap.
    - `height`: The height of the bitmap.
  - **Returns**: A transparent `Bitmap`.

### Example Usage in MainActivity

```kotlin
class MainActivity : AppCompatActivity() {

    private lateinit var imageCompareSlider: ImageCompareSlider

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        imageCompareSlider = findViewById(R.id.imageCompareSlider)

        // Example of setting up the slider with a background image
        val backgroundBitmap = // Load your bitmap here
        imageCompareSlider.setUpSlideCompare(backgroundBitmap)

        // Example of setting the foreground image
        val foregroundBitmap = // Load your bitmap here
        imageCompareSlider.setForegroundImage(foregroundBitmap)

        // Example of setting the slider's position
        imageCompareSlider.setPositionSlideImage(0.75f)
    }
}
```

### Development Notes

The `Image Compare` was developed and expanded based on the initial concept from the [Image-Comparison-Slider](https://github.com/sahildoshi013/Image-Comparison-Slider) project by `sahildoshi013`. 

In my project, I have added additional features, fixed crashes, and enhanced its functionality to better suit the needs of my company's project. These improvements include:
- Enhanced image loading capabilities to support various data types including `Bitmap`, `Drawable`, and URLs.
- Improved slider control with more precise adjustments and smoother transitions.
- Additional methods for hiding/showing images and adjusting the slider's position dynamically.

