---
title: "Visual Studio 版本中 visual c + + 工具和功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- versions [C++]
- Visual C++, versions
- editions [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2656b7e1901104b29300f5adb6647e7f3ac1db57
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="visual-c-tools-and-features-in-visual-studio-editions"></a>Visual c + + 工具和 Visual Studio 版本中的功能
下表顯示可用在 Visual Studio 中使用的 Visual C++ 功能。 儲存格中的 X 表示功能可用；空白儲存格表示功能不可用。 括號括住的附註表示功能可用，但有所限制。  
  
## <a name="platforms"></a>平台  
  
||||||  
|-|-|-|-|-|  
|平台|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio 企業版|  
|Windows 桌面||X|X|X|  
|通用 Windows 平台 ((電話、平板電腦、電腦、Xbox、IoT 和 HoloLens))|X||X|X|  
|Microsoft Store 8.1|||X|X|  
|Windows Phone 8.0|||X|X|  
|Android|||X|X|  
|iOS|||X|X|  
  
## <a name="compilers"></a>編譯器  
  
|編譯器|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio 企業版|  
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|32 位元 x86 編譯器|X|X|X|X|  
|X86_arm 跨平台編譯器|X||X|X|  
|64 位元 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 編譯器|||X|X|  
|X86_ [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 跨平台編譯器|X|X|X|X|  
  
## <a name="libraries-and-headers"></a>程式庫和標頭  
  
|程式庫或標頭|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio 企業版|  
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|Windows 標頭及程式庫和 CRT 程式庫|(X)|X|X|X|  
|C++ 標準程式庫|X|X|X|X|  
|ATL|||X|X|  
|MFC|||X|X|  
|.NET Framework 類別庫||X|X|X|  
|適用於 .NET 的 C++ 支援程式庫||X|X|X|  
|OpenMP|X|X|X|X|  
  
## <a name="project-templates"></a>專案範本  
  
|範本|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio 企業版|  
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|UWP、Windows 8.1、Windows Phone 8.0 的 XAML 範本|X||X|X|  
|Direct3D 應用程式|X||X|X|  
|DLL (通用 Windows)|X||X|X|  
|靜態程式庫 (通用 Windows)|X||X|X|  
|Windows 執行階段元件|X||X|X|  
|單元測試應用程式 (通用 Windows)|X||X|X|  
|ATL 專案|||X|X|  
|類別庫 (CLR)||X|X|X|  
|CLR 主控台應用程式||X|X|X|  
|CLR 空專案||X|X|X|  
|自訂精靈|||X|X|  
|空專案||X|X|X|  
|Makefile 專案||X|X|X|  
|MFC ActiveX 控制項|||X|X|  
|MFC 應用程式|||X|X|  
|MFC DLL|||X|X|  
|測試專案|X|X|X|X|  
|Win32 主控台應用程式||X|X|X|  
|Win32 專案||X|X|X|  
  
## <a name="tools"></a>工具  
  
|工具|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio 企業版|  
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|Incremental 連結器 (Link.exe)|X|X|X|X|  
|Program Maintenance Utility (Nmake.exe)||X|X|X|  
|程式庫產生器 (Lib.exe)|X|X|X|X|  
|Windows 資源編譯器 (Rc.exe)|X|X|X|X|  
|Windows Resource to Object Converter (CvtRes.exe)||X|X|X|  
|Browse Information Maintenance Utility (BscMake.exe)|X|X|X|X|  
|C++ 名稱 Undecorator (Undname.exe)|X|X|X|X|  
|COFF/PE 傾印工具 (Dumpbin.exe)|X|X|X|X|  
|COFF/PE 編輯器 (Editbin.exe)|X|X|X|X|  
|MASM (Ml.exe)|||X|X|  
|Spy++|||X|X|  
|ErrLook|||X|X|  
|AtlTrace|||X|X|  
|Devenv.com|||X|X|  
|推斷規則|||X|X|  
|將 VCBuild.vcproj 專案升級為 MSBuild (VCUpgrade.exe)|X|X|X|X|  
|特性指引最佳化|||X|X|  
  
## <a name="debugging-features"></a>偵錯功能  
  
|偵錯功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio 企業版|  
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|機器碼偵錯|X|X|X|X|  
|natvis (原生類型視覺效果)|X|X|X|X|  
|圖形偵錯|X||X|X|  
|Managed 偵錯||X|X|X|  
|GPU 使用量|X||X|X|  
|記憶體使用量|X||X|X|  
|遠端偵錯|X|X|X|X|  
|SQL 偵錯|||X|X|  
|靜態程式碼分析|有限|有限|X|X|  
  
## <a name="designers-and-editors"></a>設計工具和編輯器  
  
|設計工具或編輯器|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio 企業版|  
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|XAML 設計工具|X||X|X|  
|CSS 樣式設計工具/編輯器|X|X|X|X|  
|HTML 設計工具/編輯器|X|X|X|X|  
|XML 編輯器|X|X|X|X|  
|原始程式碼編輯器|X|X|X|X|  
|產能功能：重構、IntelliSense、C++ 程式碼格式化|X|X|X|X|  
|Windows Form 設計工具||X|X|X|  
|資料設計工具|||X|X|  
|原生資源編輯器 (.rc 檔)|||X|X|  
|資源編輯器|X|X|X|X|  
|模型編輯器|X||X|X|  
|著色器設計工具|X||X|X|  
  
## <a name="data-features"></a>資料功能  
  
|資料功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Premium|Visual Studio 企業版|  
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|---------------------------|------------------------------|  
|資料設計工具|||X|X|X|  
|資料物件|||X|X|X|  
|Web 服務|||X|X|X|  
|伺服器總管|||X|X|X|  
  
## <a name="build-and-project-systems"></a>建置和專案系統  
  
|建置或專案功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio 企業版|  
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|命令列組建 (msbuild.exe)|X|X|X|X|  
|原生多目標||X|X|X|  
|Managed 多目標||X|X|X|  
|平行組建|X|X|X|X|  
|組建自訂|X|X|X|X|  
|屬性頁擴充性|X|X|X|X|  
  
## <a name="automation-and-extensibility"></a>Automation 與擴充性  
  
|Automation 與擴充性|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio 企業版|  
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|擴充性物件模型|||X|X|  
|程式碼模型|||X|X|  
|專案模型|||X|X|  
|資源編輯器模型|||X|X|  
|精靈模型|||X|X|  
|偵錯工具物件模型|||X|X|  
  
## <a name="application-lifecycle-management-tools"></a>應用程式生命週期管理工具  
  
||||||  
|-|-|-|-|-|  
|工具|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio 企業版|  
|單元測試 (原生架構)|X|X|X|X|  
|單元測試 (Managed 架構)||X|X|X|  
|程式碼涵蓋範圍||||X|  
|手動測試||||X|  
|探勘測試||||X|  
|測試案例管理||||X|  
|程式碼對應和相依性圖形|||唯讀|X|  
|程式碼對應偵錯||||X|  
  
## <a name="see-also"></a>請參閱  
 [安裝 Visual Studio](/visualstudio/install/install-visual-studio)   
 [在 Visual Studio 中最新消息](/visualstudio/ide/whats-new-in-visual-studio)   
 [Visual c + + 專案類型](../ide/visual-cpp-project-types.md)   
 [Visual Database Tools 版本](http://msdn.microsoft.com/en-us/a7689adc-f16b-4cc7-b6fe-39ca0c711161)