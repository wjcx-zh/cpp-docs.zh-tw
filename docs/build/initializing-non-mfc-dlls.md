---
title: "初始化非 MFC DLL | Microsoft Docs"
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
  - "DLL [C++], 非 MFC"
  - "初始化 DLL"
  - "非 MFC DLL [C++]"
ms.assetid: 2622b32a-28f9-4d61-9e46-6c19aaf8b7ad
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 初始化非 MFC DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要初始化非 MFC DLL，您的 DLL 原始程式碼必須包含名為 `DllMain` 的函式。  下列程式碼會展示一個可以說明 `DllMain` 定義的基本架構：  
  
```  
BOOL APIENTRY DllMain(HANDLE hModule,   
                      DWORD  ul_reason_for_call,   
                      LPVOID lpReserved)  
{  
    switch( ul_reason_for_call ) {  
    case DLL_PROCESS_ATTACH:  
    ...  
    case DLL_THREAD_ATTACH:  
    ...  
    case DLL_THREAD_DETACH:  
    ...  
    case DLL_PROCESS_DETACH:  
    ...  
    }  
    return TRUE;  
}  
```  
  
> [!NOTE]
>  **DllEntryPoint** 的 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 文件指出，進入點函式的實際名稱必須在連結器命令列搭配 \/ENTRY 選項指定。  在 Visual C\+\+ 中，如果您的進入點函式的名稱是 `DllMain`，您就不用使用 \/ENTRY 選項。  事實上，如果您使用 \/ENTRY 選項，並且將您的進入點函式命名為 `DllMain` 以外的名稱，C 執行階段程式庫就無法適當地初始化。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [\<caps:sentence id\="tgt7" sentenceid\="58bb7328659bda9ffb73a1dcd39da06b" class\="tgtSentence"\>DllMain 的函式規格 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682583)  
  
-   [\<caps:sentence id\="tgt8" sentenceid\="f29344705c59343b34b642944921cbdf" class\="tgtSentence"\>動態連結程式庫的進入點函式 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682596)  
  
-   [C 執行階段程式庫行為和 \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
## 請參閱  
 [初始化 DLL](../build/initializing-a-dll.md)