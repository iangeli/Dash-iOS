project 'Dash/Dash iOS.xcodeproj'
platform :ios, "13.0"

target "Dash" do
  inhibit_all_warnings!
  
  pod 'MRProgress', :path => 'Modified Pods/MRProgress/MRProgress.podspec'
  # Commented out a bunch of stuff in MRBlurView's redraw, otherwise the overlay progress makes the entire screen flicker when it is first shown
  # MRStopButton has support for whole sizes (their calculations ended up with non-integral frames)
  # Also overwrote pointInside: for MRCircularProgressView...
  # Removed AccessibilityValueChangeNotify because it causes VoiceOver to stall
  pod 'KissXML', :path => 'Modified Pods/KissXML-5.1.2/KissXML.podspec'
  # Modified to make addChild: remove parent
  pod 'UIAlertView+Blocks'
  pod 'UIActionSheet+Blocks'
  pod 'AutoCoding'
  pod 'DZNEmptyDataSet', :git => 'https://github.com/benrudhart/DZNEmptyDataSet.git'
  pod 'JGMethodSwizzler'
  pod 'DTBonjour', :path => 'Modified Pods/DTBonjour/DTBonjour.podspec'
  # Modified to add originating IP address support to DTBonjourDataConnection
  # Also modified to send a delegate message when a connection closes
  # Replaced asserts() with ifs() in DTBonjourServer start
  
  pod 'Reachability'
  pod 'SAMKeychain'
  pod 'NSTimer-Blocks'
  pod 'GZIP'
  pod 'Masonry'
  pod 'SnapKit'
end

post_install do | installer |
  require 'fileutils'
  FileUtils.cp_r('Pods/Target Support Files/Pods-Dash/Pods-Dash-acknowledgements.plist', 'Dash/Settings.bundle/Cocoa_Pods_Acknowledgements.plist', :remove_destination => true)
  
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      if config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'].to_f < 13.0
        config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '13.0'
      end
    end
  end
end
