---
title: "初始化 DLL | Microsoft Docs"
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
  - "DLL [C++], 初始化"
  - "初始化 DLL"
  - "終止程式碼 [C++]"
ms.assetid: f655c5ff-ab5b-493a-a1da-4d1074e60c5b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 初始化 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一般說來，您的 DLL 會有必須在 DLL 載入時執行的初始化程式碼 \(例如，配置記憶體\)。  使用 Visual C\+\+ 時，要在何處加入程式碼以初始化 DLL，會取決於所建置的 DLL 類型。  如果您不需要加入初始化或終止程式碼，在建置 DLL 時就不需要執行特定步驟。  下表列出當您要初始化 DLL 時的程式碼加入位置說明。  
  
|DLL 類型|加入初始化和終止程式碼的位置|  
|------------|--------------------|  
|標準 DLL|DLL 的 `CWinApp` 物件的 `InitInstance` 和 `ExitInstance`|  
|擴充 DLL|MFC DLL 精靈產生的 `DllMain` 函式|  
|非 MFC DLL|由您提供名稱為 `DllMain` 的函式|  
  
 在 Win32 中，所有的 DLL 可能會包含選擇性 \(Optional\) 的進入點函式 \(通常稱為 `DllMain`\)，在初始化和終止時都會呼叫此函式。  這樣您就有機會根據需求來配置或釋放其他的資源。  Windows 在下列四種情況下會呼叫進入點函式：處理序連結、處理序中斷連結、執行緒連結和執行緒中斷連結。  
  
 C 執行階段程式庫會提供名為 **\_DllMainCRTStartup** 的進入點函式，並且呼叫 `DllMain`。  根據 DLL 類型，您應該在原始程式碼中提供名稱為 `DllMain` 的函式，或者使用 MFC 程式庫提供的 `DllMain`。  
  
## 您想要執行甚麼工作？  
  
-   [初始化標準 DLL](../build/initializing-regular-dlls.md)  
  
-   [初始化擴充 DLL](../build/initializing-extension-dlls.md)  
  
-   [初始化非 MFC DLL](../build/initializing-non-mfc-dlls.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [C 執行階段程式庫行為和 \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
-   [\<caps:sentence id\="tgt24" sentenceid\="58bb7328659bda9ffb73a1dcd39da06b" class\="tgtSentence"\>DllMain 的函式規格 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682583)  
  
-   [\<caps:sentence id\="tgt25" sentenceid\="f29344705c59343b34b642944921cbdf" class\="tgtSentence"\>動態連結程式庫的進入點函式 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682596)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)