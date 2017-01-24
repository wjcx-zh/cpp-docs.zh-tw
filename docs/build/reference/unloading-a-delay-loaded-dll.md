---
title: "卸載延遲載入的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__FUnloadDelayLoadedDLL2"
  - "DLL 的延遲載入, 未載入"
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 卸載延遲載入的 DLL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

預設提供的延遲載入 Helper 會檢查延遲載入描述項是否已經有指標，以及在 pUnloadIAT 欄位中是否有一份原本匯入位址表 \(IAT\) 的複本。  如果有，它會將清單中的指標儲存至匯入延遲描述項中。  這樣使得 Helper 函式可以以名稱找出 DLL，以便支援明確卸載該 DLL。  
  
 以下是明確卸載延遲載入 DLL 的相關結構和函式：  
  
```  
//  
// Unload support from delayimp.h  
//  
  
// routine definition; takes a pointer to a name to unload  
  
ExternC  
BOOL WINAPI  
__FUnloadDelayLoadedDLL2(LPCSTR szDll);  
  
// structure definitions for the list of unload records  
typedef struct UnloadInfo * PUnloadInfo;  
typedef struct UnloadInfo {  
    PUnloadInfo     puiNext;  
    PCImgDelayDescr pidd;  
    } UnloadInfo;  
  
// from delayhlp.cpp  
// the default delay load helper places the unloadinfo records in the   
// list headed by the following pointer.  
ExternC  
PUnloadInfo __puiHead;  
```  
  
 使用 **LocalAlloc** 和 **LocalFree** 實作分別做為其運算子 **new** 和 **delete** 的 C\+\+ 類別可以實作 UnloadInfo 結構。  這些選項保存於使用 \_\_puiHead 做為清單標頭的標準連結清單中。  
  
 呼叫 \_\_FUnloadDelayLoadedDLL 將試著找出您在載入 DLL 清單中提供的名稱 \(必須完全相符\)。  如果有找到，pUnloadIAT 中的 IAT 將被複製到執行中之 IAT 上方以復原 Thunk 指標，然後程式庫將被 **FreeLibrary** 釋放，而符合的 **UnloadInfo** 記錄將從清單中解除連結並刪除，最後傳回 TRUE。  
  
 函式 \_\_FUnloadDelayLoadedDLL2 的引數會區分大小寫。  例如，您會指定：  
  
```  
__FUnloadDelayLoadedDLL2("user32.DLL");  
```  
  
 而非：  
  
```  
__FUnloadDelayLoadedDLL2("User32.DLL");.  
```  
  
## 請參閱  
 [Understanding the Helper Function](http://msdn.microsoft.com/zh-tw/6279c12c-d908-4967-b0b3-cabfc3e91d3d)