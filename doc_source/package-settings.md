# Package settings<a name="package-settings"></a>


|  | 
| --- |
| The model packaging feature is in preview release for Amazon Lookout for Vision and is subject to change\. | 

Use the following information to decide the package settings for your model packaging job\.

To create a model packaging job, see [Packaging your model \(Console\)](package-job-console.md) or [Packaging your model \(SDK\)](package-job-sdk.md)\. 

**Topics**
+ [Target hardware](#package-settings-target-hardware)
+ [Component settings](#package-settings-component-settings)

## Target hardware<a name="package-settings-target-hardware"></a>

You can choose a target device or target platform for your model, but not both\. For more information, see [Tested devices, chip architectures, and operating systems](models-devices-setup-requirements.md#models-devices-setup-core-device-tested)\. 

**Target device**  
The target device for the model, such as [NVIDIA® Jetson AGX Xavier](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-agx-xavier/)\. 

**Target platform**  
Amazon Lookout for Vision supports the X86\_64 \(64\-bit version of the x86 instruction set\) and ARM\_64 \(ARMv8 64\-bit CPU\) architectures\. Lookout for Vision supports the Linux operating system and various NVIDIA accelerators\. 

### Compiler options<a name="package-settings-compiler-options"></a>

Compiler options allow you to specify the correct hardware or device options  for your AWS IoT Greengrass Version 2 core device\. Currently you can specify the following compiler options, which are required for the NVIDIA accelerator \(target platform\) and NVIDIA Jetson Xavier \(target device\):
+ `gpu-code` — Specifies the gpu code of the core device that runs the model component\. Not required when you target a Jetson Xavier target device\. 
+ `trt-ver` — Specifies the TensorRT version in x\.y\.z\. format\.
+ `cuda-ver` — Specifies the CUDA version in x\.y format\.

You specify the options in JSON format\. For example:

```
{'gpu-code': 'sm_72', 'trt-ver': '6.0.1', 'cuda-ver': '10.1'}
```

For more examples, see [Tested devices, chip architectures, and operating systems](models-devices-setup-requirements.md#models-devices-setup-core-device-tested)\.

## Component settings<a name="package-settings-component-settings"></a>

The model packaging job creates a model component that contains your model\. The job creates artifacts that AWS IoT Greengrass V2 uses to deploy the model component to the core device\. 

 You can't create a model component with the same component name and component version as an existing component\. 

**Component name**  
A name for the model component that Lookout for Vision creates during model packaging\. The component name you specify is displayed in the AWS IoT Greengrass V2 console\. 

**Component description**  
\(Optional\) A description for the model component\.

**Component version**  
A version number for the model component\. You can accept the default version number or choose your own\. The version number must follow the semantic version number system – major\.minor\.patch\. For example, version 1\.0\.0 represents the first major release for a component\. For more information, see [Semantic Versioning 2\.0\.0](https://semver.org/)\. If you don't provide a value, Lookout for Vision uses the version number of your model to generate a version for you\. 

**Component location**  
The Amazon S3 location where you want the model packaging job to save the model component artifacts\. The Amazon S3 bucket must be in the same AWS Region and AWS account in which you use AWS IoT Greengrass Version 2\. To create an Amazon S3 bucket, see [Creating a bucket](https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html)\. 

**Tags**  
You can identify, organize, search for, and filter your components by using tags\. Each tag is a label consisting of a user\-defined key and value\. The tags are attached to the model component when the model packaging job creates the model component in Greengrass\. A component is an AWS IoT Greengrass V2 resource\. The tags aren't attached to any of your Lookout for Vision resources, such as your models\. For more information, see [Tagging AWS resources](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html)\. 