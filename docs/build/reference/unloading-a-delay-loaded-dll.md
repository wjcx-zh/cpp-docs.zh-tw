---
title: "卸載延遲載入 DLL |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b47969da4c560f28c07ac09caef83873e362ddc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="unloading-a-delay-loaded-dll"></a>卸載延遲載入的 DLL
預設提供的延遲載入 helper 會檢查以查看延遲載入描述元 pUnloadIAT 欄位中是否有一個指標，以及原始匯入位址表 (IAT)。 若是如此，它會將指標儲存至匯入的延遲描述項清單中。 這可讓 helper 函式，以尋找 DLL 支援明確卸載該 DLL 的名稱。  
  
 以下是相關聯的結構和函式的明確卸載延遲載入 DLL:  
  
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
  
 使用 c + + 類別實作 UnloadInfo 結構**LocalAlloc**和**LocalFree**作為其運算子的實作**新**和運算子**刪除**分別。 這些選項會保留在使用 __puihead 做為清單的開頭的標準連結清單。  
  
 呼叫 __FUnloadDelayLoadedDLL 就會嘗試尋找名稱中載入的 dll （確切的相符項目是必要的） 提供。 如果找不到，pUnloadIAT 中 IAT 的副本複製執行 IAT 還原 thunk 指標頂端，透過將程式庫會釋出與**FreeLibrary**，比對**UnloadInfo**記錄從連結清單和刪除，而且會傳回 TRUE。  
  
 函式 __FUnloadDelayLoadedDLL2 的引數是區分大小寫。 例如，您會指定：  
  
```  
__FUnloadDelayLoadedDLL2("user32.DLL");  
```  
  
 而不是：  
  
```  
__FUnloadDelayLoadedDLL2("User32.DLL");.  
```  
  
## <a name="see-also"></a>請參閱  
 [了解協助協助程式函式](understanding-the-helper-function.md)