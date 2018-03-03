---
title: "告知攔截 |Microsoft 文件"
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
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 31490e3bb591af6568ffecddf68219c89a25e055
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="notification-hooks"></a>告知攔截
告知攔截稱為之前在 helper 常式會執行下列動作：  
  
-   儲存至程式庫的控制代碼會檢查是否已載入。  
  
-   **LoadLibrary**呼叫以嘗試載入的 dll。  
  
-   **GetProcAddress**呼叫以嘗試取得程序的位址。  
  
-   傳回以延遲匯入負載 thunk。  
  
 告知攔截會啟用：  
  
-   藉由提供新定義的指標**__pfnDliNotifyHook2** ，初始化以指向自己收到通知的函式。  
  
     -或-  
  
-   藉由設定指標**__pfnDliNotifyHook2**來攔截函式之前呼叫任何程式的 DLL 延遲載入。  
  
 如果通知，則**dliStartProcessing**，攔截函式可以傳回：  
  
 NULL  
 預設的協助程式處理 DLL 的載入。 這非常有用呼叫只供使用者參考。  
  
 函式指標  
 略過預設延遲載入的處理。 這可讓您提供您自己的載入處理常式。  
  
 如果通知，則**dliNotePreLoadLibrary**，攔截函式可以傳回：  
  
-   0，如果它只想資訊通知。  
  
-   載入 DLL 時，如果它載入該 DLL 本身的 HMODULE。  
  
 如果通知，則**dliNotePreGetProcAddress**，攔截函式可以傳回：  
  
-   0，如果它只想資訊通知。  
  
-   匯入函式的位址，如果攔截函式取得本身的位址。  
  
 如果通知，則**dliNoteEndProcessing**，攔截函式的傳回值會被忽略。  
  
 如果此指標初始化 （非零），延遲載入 helper 會叫用函式在整個執行期間的特定通知點。 函式指標都具有下列定義：  
  
```  
// The "notify hook" gets called for every call to the  
// delay load helper.  This allows a user to hook every call and  
// skip the delay load helper entirely.  
//  
// dliNotify == {  
//  dliStartProcessing |  
//  dliNotePreLoadLibrary  |  
//  dliNotePreGetProc |  
//  dliNoteEndProcessing}  
//  on this call.  
//  
ExternC  
PfnDliHook   __pfnDliNotifyHook2;  
  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 通知傳入**DelayLoadInfo**攔截函式，以及通知值的結構。 此資料是相同的延遲載入 helper 常式所使用。 通知值將會是其中一個定義中的值[結構和常數定義](../../build/reference/structure-and-constant-definitions.md)。  
  
## <a name="see-also"></a>請參閱  
 [錯誤處理和通知](../../build/reference/error-handling-and-notification.md)