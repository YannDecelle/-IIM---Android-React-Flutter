To manually update `settings.gradle`, follow these steps:

    1. Copy `settings.gradle` as `settings_aar.gradle`
    2. Remove the following code from `settings_aar.gradle`:

        def localPropertiesFile = new File(rootProject.projectDir, "local.properties")
        def properties = new Properties()

        assert localPropertiesFile.exists()
        localPropertiesFile.withReader("UTF-8") { reader -> properties.load(reader) }

        def flutterSdkPath = properties.getProperty("flutter.sdk")
        assert flutterSdkPath != null, "flutter.sdk not set in local.properties"
        apply from: "$flutterSdkPath/packages/flutter_tools/gradle/app_plugin_loader.gradle"