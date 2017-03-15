---
title: "/GZ (啟用堆疊框架執行階段錯誤檢查) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gz"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GZ 編譯器選項 [C++]"
  - "偵錯組建, 攔截發行組建的錯誤"
  - "GZ 編譯器選項 [C++]"
  - "-GZ 編譯器選項 [C++]"
  - "發行組建的錯誤"
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /GZ (啟用堆疊框架執行階段錯誤檢查)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所執行的作業與 [\/RTC \(執行階段錯誤檢查\)](../../build/reference/rtc-run-time-error-checks.md) 選項相同，  已取代。  
  
## 語法  
  
```  
/GZ  
```  
  
## 備註  
 **\/GZ** 只用在非最佳化的 \([\/Od \(停用 \(偵錯\)\)](../../build/reference/od-disable-debug.md)\) 組建中。  
  
 **\/GZ** 已被取代。請改用 [\/RTC \(執行階段錯誤檢查\)](../../build/reference/rtc-run-time-error-checks.md)。  如需詳細資訊，請參閱[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)