---
title: "專案檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".vcproj 檔案"
  - "專案檔 [C++], .vcproj 檔案格式"
  - "VCPROJ (Visual C++ 專案檔) 格式"
  - "Visual C++ 專案, 專案檔格式"
ms.assetid: 5261cf45-3136-40a6-899e-dc1339551401
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 專案檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 專案檔是副檔名為 .vcxproj 的 XML 架構檔案，其中包含建置 Visual C\+\+ 專案所需的資訊。  
  
## 範例  
 下列範例 .vcxproj 檔是在 \[**新增專案**\] 對話方塊中指定 \[**Win32 主控台應用程式**\] 而產生。  若要處理專案檔，請在命令列中使用 msbuild.exe 工具，或在 [!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)] 中使用 \[**建置**\] 命令 \(無法處理此範例，因為未提供所需的原始程式檔和標頭檔\)。如需專案檔中 XML 項目的詳細資訊，請參閱 [Project File Schema Reference](../Topic/MSBuild%20Project%20File%20Schema%20Reference.md)。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup Label="ProjectConfigurations">  
    <ProjectConfiguration Include="Debug|Win32">  
      <Configuration>Debug</Configuration>  
      <Platform>Win32</Platform>  
    </ProjectConfiguration>  
    <ProjectConfiguration Include="Release|Win32">  
      <Configuration>Release</Configuration>  
      <Platform>Win32</Platform>  
    </ProjectConfiguration>  
  </ItemGroup>  
  <PropertyGroup Label="Globals">  
    <ProjectGuid>{96F21549-A7BF-4695-A1B1-B43625B91A14}</ProjectGuid>  
    <Keyword>Win32Proj</Keyword>  
    <RootNamespace>SomeProjName</RootNamespace>  
  </PropertyGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />  
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">  
    <ConfigurationType>Application</ConfigurationType>  
    <CharacterSet>Unicode</CharacterSet>  
  </PropertyGroup>  
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
    <ConfigurationType>Application</ConfigurationType>  
    <WholeProgramOptimization>true</WholeProgramOptimization>  
    <CharacterSet>Unicode</CharacterSet>  
  </PropertyGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
  <ImportGroup Label="ExtensionSettings">  
  </ImportGroup>  
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">  
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />  
  </ImportGroup>  
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">  
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />  
  </ImportGroup>  
  <PropertyGroup Label="UserMacros" />  
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">  
    <LinkIncremental>true</LinkIncremental>  
  </PropertyGroup>  
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">  
    <LinkIncremental>false</LinkIncremental>  
  </PropertyGroup>  
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">  
    <ClCompile>  
      <PrecompiledHeader>Use</PrecompiledHeader>  
      <WarningLevel>Level3</WarningLevel>  
      <MinimalRebuild>true</MinimalRebuild>  
      <DebugInformationFormat>EditAndContinue</DebugInformationFormat>  
      <Optimization>Disabled</Optimization>  
      <BasicRuntimeChecks>EnableFastChecks</BasicRuntimeChecks>  
      <RuntimeLibrary>MultiThreadedDebugDLL</RuntimeLibrary>  
      <PreprocessorDefinitions>WIN32;_DEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>  
    </ClCompile>  
    <Link>  
      <SubSystem>Console</SubSystem>  
      <GenerateDebugInformation>true</GenerateDebugInformation>  
    </Link>  
  </ItemDefinitionGroup>  
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">  
    <ClCompile>  
      <WarningLevel>Level3</WarningLevel>  
      <PrecompiledHeader>Use</PrecompiledHeader>  
      <DebugInformationFormat>ProgramDatabase</DebugInformationFormat>  
      <Optimization>MaxSpeed</Optimization>  
      <RuntimeLibrary>MultiThreadedDLL</RuntimeLibrary>  
      <FunctionLevelLinking>true</FunctionLevelLinking>  
      <IntrinsicFunctions>true</IntrinsicFunctions>  
      <PreprocessorDefinitions>WIN32;NDEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>  
    </ClCompile>  
    <Link>  
      <SubSystem>Console</SubSystem>  
      <GenerateDebugInformation>true</GenerateDebugInformation>  
      <EnableCOMDATFolding>true</EnableCOMDATFolding>  
      <OptimizeReferences>true</OptimizeReferences>  
    </Link>  
  </ItemDefinitionGroup>  
  <ItemGroup>  
    <None Include="ReadMe.txt" />  
  </ItemGroup>  
  <ItemGroup>  
    <ClInclude Include="stdafx.h" />  
    <ClInclude Include="targetver.h" />  
  </ItemGroup>  
  <ItemGroup>  
    <ClCompile Include="SomeProjName.cpp" />  
    <ClCompile Include="stdafx.cpp">  
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">Create</PrecompiledHeader>  
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">Create</PrecompiledHeader>  
    </ClCompile>  
  </ItemGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />  
  <ImportGroup Label="ExtensionTargets">  
  </ImportGroup>  
</Project>  
```  
  
## 請參閱  
 [在 Visual Studio 中建置 C\+\+ 專案](../ide/building-cpp-projects-in-visual-studio.md)   
 [使用專案屬性](../ide/working-with-project-properties.md)