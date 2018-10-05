source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '8.0'
use_frameworks!


target 'PassportScannerNs' do
    pod 'TesseractOCRiOS'
    pod 'UIImage-Resize'
    pod 'GPUImage'
    pod 'EVGPUImage2'
 end

post_install do |installer|
    if target.name == 'TesseractOCRiOS' 
            target.build_configurations.each do |config|
                config.build_settings['ENABLE_BITCODE'] = 'NO'
            end
            header_phase = target.build_phases().select do |phase|
                phase.is_a? Xcodeproj::Project::PBXHeadersBuildPhase
            end.first

            duplicated_header_files = header_phase.files.select do |file|
                file.display_name == 'config_auto.h'
            end

            duplicated_header_files.each do |file|
                header_phase.remove_build_file file
            end
        end
end


