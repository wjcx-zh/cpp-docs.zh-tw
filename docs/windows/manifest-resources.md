---
title: "資訊清單資源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 56a41a7901e41f4c76fbb9fcbf5930ec97c3b866
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="manifest-resources"></a>資訊清單資源
資訊清單資源是描述應用程式所用相依性的 XML 檔案。 例如，在 Visual Studio 中，MFC 精靈產生的資訊清單檔案會定義應用程式應該使用哪些 Windows 通用控制項 DLL (5.0 或 6.0 版)：  
  
```  
<description>Your app description here</description>   
<dependency>   
    <dependentAssembly>   
        <assemblyIdentity   
            type="win32"   
            name="Microsoft.Windows.Common-Controls"   
            version="6.0.0.0"   
            processorArchitecture="X86"   
            publicKeyToken="6595b64144ccf1df"   
            language="*"   
        />   
    </dependentAssembly>   
</dependency>   
```  
  
 對於 Windows XP 或 Windows Vista 應用程式，資訊清單資源不只會指定應用程式使用最新版的 Windows 通用控制項 (v6.0，如上所示)，也會支援 [Syslink 控制項](http://msdn.microsoft.com/library/windows/desktop/bb760706)。  
  
 若要檢視資訊清單資源內含的版本和類型資訊，您可以在 XML 檢視器或在 Visual Studio [文字編輯器](http://msdn.microsoft.com/en-us/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)中開啟此檔案。 如需詳細資訊，請參閱 [在 Visual Studio 文字編輯器中開啟資訊清單資源](../windows/how-to-open-a-manifest-resource.md)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱  [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
## <a name="limitations"></a>限制  
 每個模組只能有一個資訊清單資源。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [控制項](../mfc/controls-mfc.md)   
 [使用資源檔](../windows/working-with-resource-files.md)