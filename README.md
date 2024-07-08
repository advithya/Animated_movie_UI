# animated_movies_app

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

### Installation Steps
#### Prerequisites
1. **Flutter SDK**: Ensure you have Flutter installed. Follow the [official Flutter installation guide](https://flutter.dev/docs/get-started/install) for your operating system.
2. **CMake**: Required for building the project on Linux and Windows. Install it from [CMake's official site](https://cmake.org/download/).
3. **Android Studio**: Required for building the Android version. Install it from [Android Studio's official site](https://developer.android.com/studio).

#### Steps
1. **Clone the Repository**:
   git clone <repository_url>
    cd <repository_directory> 
2. **Install Flutter Dependencies**:
       flutter pub get
3. **Platform-Specific Steps**:
    - **Android**:
        1. Open the project in Android Studio.
        2. Ensure that the `local.properties` file is correctly set up with the path to your Flutter SDK.
        3. Build and run the project using Android Studio.
    - **Linux**:
        1. Ensure you have the necessary dependencies:
                       sudo apt-get install cmake pkg-config gtk+-3.0
        2. Create a build directory and run CMake:
                       mkdir build
            cd build
            cmake ..
            make
        3. Run the application:
                       ./animated_movies_app
    - **Windows**:
        1. Open a terminal and navigate to the project directory.
        2. Create a build directory and run CMake:
                       mkdir build
            cd build
            cmake ..
            cmake --build . --config Release
        3. Run the application:
           .\Release\animated_movies_app.exe
### References to Code Blocks
- **Linux CMakeLists.txt**:
- **Windows CMakeLists.txt**:
- **Android build.gradle**:
- **Flutter Animation Route**:
       
### Key Features 
1. **Custom Navigation Animations**: 
   - The app uses custom zoom navigation animations for transitioning between screens.
   - Reference:
     
// Custom zoom navigation animation
Route zoomNavigation(Widget page) {
  return PageRouteBuilder(
    transitionDuration: const Duration(milliseconds: 600),
    pageBuilder: (context, animation, secondaryAnimation) => page,
    transitionsBuilder: (context, animation, secondaryAnimation, page) {
      var begin = 0.0;
      var end = 1.0;
      var curve = Curves.ease;

      var tween = Tween(begin: begin, end: end).chain(CurveTween(curve: curve));
      return ScaleTransition(
        scale: animation.drive(tween),
        child: page,
      );
    },
  );
}
2. **Onboarding Screen**:
   - The onboarding screen features a marquee effect to display a list of movies.
   - Reference:
 import 'package:animated_movies_app/constants/route_animation.dart';
import 'package:animated_movies_app/constants/ui_constant.dart';
import 'package:animated_movies_app/screens/home_screen/home_screen.dart';
import 'package:animated_movies_app/screens/onboarding_screen/widgets/custom_marquee_widget.dart';
import 'package:flutter/material.dart';
import 'package:marqueer/marqueer.dart';
3. **Home Screen**:
   - The home screen includes an animated stack of movie covers that users can interact with.
   - Reference:
     import 'package:animated_movies_app/constants/ui_constant.dart';
import 'package:animated_movies_app/data/movies_data.dart';
import 'package:animated_movies_app/screens/detail_screen/detail_screen.dart';
import 'package:animated_movies_app/screens/home_screen/widgets/animated_stack.dart';
import 'package:animated_movies_app/screens/home_screen/widgets/bottom_nav_bar.dart';
import 'package:animated_movies_app/screens/home_screen/widgets/filters_widget.dart';
import 'package:animated_movies_app/screens/home_screen/widgets/header_widget.dart';
import 'package:animated_movies_app/screens/home_screen/widgets/movies_cover_widget.dart';
import 'package:animated_movies_app/screens/home_screen/widgets/search_field_widget.dart';
import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});
  @override
  Widget build(BuildContext context) {
    final size = MediaQuery.sizeOf(context);
    return Scaffold(
      body: Container(
        height: size.height,
        width: size.width,
        decoration: UiConstants.backgroundGradient,
        child: SingleChildScrollView(
4. **Detail Screen**:
   - The detail screen provides comprehensive information about a selected movie, including a cover image, plot, and cast.
   - Reference:
     import 'package:animated_movies_app/screens/detail_screen/widgets/movie_cover_and_play_button_widget.dart';
import 'package:animated_movies_app/screens/detail_screen/widgets/movie_info_and_rating.dart';
import 'package:animated_movies_app/screens/detail_screen/widgets/movies_cast.dart';
import 'package:animated_movies_app/screens/detail_screen/widgets/plot_widget.dart';
import 'package:animated_movies_app/screens/detail_screen/widgets/watch_now_button.dart';
import 'package:flutter/material.dart';
5. **Splash Screen**:
   - The splash screen automatically navigates to the onboarding screen after a delay.
   - Reference:
     import 'package:animated_movies_app/screens/onboarding_screen/onboarding_screen.dart';
import 'package:flutter/material.dart';
import 'package:lottie/lottie.dart';

class SplashScreen extends StatefulWidget {
  const SplashScreen({super.key});

  @override
  State<SplashScreen> createState() => _SplashScreenState();
}

class _SplashScreenState extends State<SplashScreen> {
  @override
  void initState() {
    super.initState();
    _navigateToOnboardingScreen();
  }

  // Navigating to Onboarding screen automatically after 2 seconds
  _navigateToOnboardingScreen() {
    Future.delayed(const Duration(seconds: 2), () {
      Navigator.of(context).pushReplacement(
        MaterialPageRoute(
          builder: (context) => const OnboardingScreen(),
        ),
      );
    });
  }

    
    
