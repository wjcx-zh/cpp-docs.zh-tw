---
title: "告知攔截 | Microsoft Docs"
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
  - "DLL 的延遲載入, 告知攔截"
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 告知攔截
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 Helper 常式中，告知攔截會在下列動作執行之前被呼叫：  
  
-   檢查程式庫中儲存的控制代碼，以確認是否已經載入。  
  
-   呼叫 **LoadLibrary** 以試著載入 DLL。  
  
-   呼叫 **GetProcAddress** 以試著取得程序的位址。  
  
-   傳回延遲匯入載入 Thunk。  
  
 告知攔截以下列方法啟用：  
  
-   為指標 **\_\_pfnDliNotifyHook2** 提供新的定義，此指標被初始化為指向您自己接收告知的函式。  
  
     \-或\-  
  
-   藉由在對程式延遲載入的 DLL 進行任何呼叫之前，將指標 **\_\_pfnDliNotifyHook2** 設定為指向攔截函式。  
  
 如果告知是 **dliStartProcessing**，攔截函式可傳回：  
  
 NULL  
 預設 Helper 處理 DLL 的載入。  只有因為資訊目地而呼叫時，才會有效用。  
  
 函式指標  
 略過預設的延遲載入處理。  這讓您可以提供自己的載入處理常式。  
  
 如果告知是 **dliNotePreLoadLibrary**，攔截函式可傳回：  
  
-   如果它只需要資訊告知則傳回 0。  
  
-   如果它自行載入 DLL 則傳回載入 DLL 的 HMODULE。  
  
 如果告知是 **dliNotePreGetProcAddress**，攔截函式可傳回：  
  
-   如果它只需要資訊告知則傳回 0。  
  
-   如果攔截函式自行取得位址，則傳回匯入函式的位址。  
  
 如果告知是 **dliNoteEndProcessing**，攔截函式的傳回值將被忽略。  
  
 如果這個指標已經初始化 \(非零\)，則延遲載入 Helper 將於整個執行期間的特定告知點叫用 \(Invoke\) 函式。  函式指標具有下列定義：  
  
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
  
 告知在 **DelayLoadInfo** 結構中連同告知值傳遞到攔截函式。  這個資料與延遲載入 Helper 常式所使用的資料完全相同。  告知值為[結構和常數定義](../../build/reference/structure-and-constant-definitions.md)中所定義值的其中一個。  
  
## 請參閱  
 [錯誤處理和告知](../../build/reference/error-handling-and-notification.md)