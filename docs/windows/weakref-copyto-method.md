---
title: "WeakRef::CopyTo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef::CopyTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CopyTo 方法"
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# WeakRef::CopyTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指派介面指標 \(如有提供\) 給指定的指標變數。  
  
## 語法  
  
```  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<  
   typename U  
>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
#### 參數  
 `U`  
 IInspectable 介面的指標。 若 `U` 不是衍生自 IInspectable，會發出錯誤。  
  
 `riid`  
 介面識別碼。 若 `riid` 不是衍生自 **IWeakReference**，會發出錯誤。  
  
 `ptr`  
 IInspectable 或 IWeakReference 雙向間接指標。  
  
## 傳回值  
 若成功，則為 S\_OK，否則會是 HRESULT 指出失敗。 如需詳細資訊，請參閱＜備註＞。  
  
## 備註  
 傳回值 S\_OK 只表示此作業已成功，而不會指出是否已將弱式參考解析為強式參考。 若傳回 S\_OK，請測試參數 `p` 為強式參考，亦即參數 `p` 不等於 `nullptr`。  
  
 自 Windows 10 SDK 起，若無法取得弱式參考，此方法便不會將 WeakRef 執行個體設為 `nullptr`，因此您應避免會檢查 WeakRef 是否為 `nullptr` 的錯誤檢查程式碼。 相反地，請檢查傳回的 HRESULT，以判斷此方法是否成功，或檢查 `ptr` 是否有 `nullptr`。  
  
## 需求  
 **標頭：**client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [WeakRef 類別](../windows/weakref-class.md)