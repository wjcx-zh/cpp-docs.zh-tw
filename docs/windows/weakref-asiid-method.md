---
title: "WeakRef::AsIID 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef::AsIID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsIID 方法"
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# WeakRef::AsIID 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

設定指定的 ComPtr 指標參數，以代表指定的介面識別碼。  
  
## 語法  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
#### 參數  
 `riid`  
 介面識別碼。  
  
 `ptr`  
 這項作業完成時，表示參數 `riid` 的物件。  
  
## 傳回值  
  
-   如果作業成功，為 S\_OK；否則為表示作業失敗原因的 HRESULT，且 `ptr` 設為 `nullptr`。  
  
-   如果作業成功，為 S\_OK，但已釋放目前的 WeakRef 物件。 參數 `ptr` 設定為 `nullptr`。  
  
-   如果作業成功，為 S\_OK，但目前的 WeakRef 物件不是衍生自參數 `riid`。 參數 `ptr` 設定為 `nullptr`。 \(如需詳細資訊，請參閱＜備註＞\)。  
  
## 備註  
 如果參數 `riid` 不是衍生自 IInspectable，則會發出錯誤。 這個錯誤會取代傳回值。  
  
 第一個範本是程式碼中應該使用的表單。 第二個範本 \(此處未顯示但會在標頭檔中宣告\) 是支援 C\+\+ 語言功能的內部協助程式特製化，例如 [auto](../cpp/auto-cpp.md) 類型推斷關鍵字。  
  
 從 Windows 10 SDK 開始，如果無法取得弱式參考，這個方法不會將 WeakRef 執行個體設定為 `nullptr`，因此您應該避免檢查錯誤的程式碼，檢查 WeakRef 有沒有 `nullptr`。 相反地，請檢查傳回的 HRESULT，以判斷此方法是否成功，或檢查 `ptr` 是否有 `nullptr`。  
  
## 需求  
 **標頭：**client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [WeakRef 類別](../windows/weakref-class.md)