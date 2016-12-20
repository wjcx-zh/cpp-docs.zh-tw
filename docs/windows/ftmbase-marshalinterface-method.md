---
title: "FtmBase::MarshalInterface 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::MarshalInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MarshalInterface 方法"
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::MarshalInterface 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

寫入所要求的資料至資料流中以初始化某個用戶端處理序中的 Proxy 物件。  
  
## 語法  
  
```  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
#### 參數  
 `pStm`  
 在封送處理期間所要使用之資料流的指標。  
  
 `riid`  
 要封送處理的介面識別項的參考。  必須以 IUnknown 介面衍生這個介面。  
  
 `pv`  
 要封送處理介面的指標;如果呼叫端沒有所需的介面指標，則可為 NULL。  
  
 `dwDestContext`  
 要解除指定介面封送處理的目的端內容。  
  
 指定一或多個 MSHCTX 列舉值。  
  
 Unmarshaling 可能發生在目前處理序 \(MSHCTX\_INPROC\) 的另一個 Apartment 或在同一個電腦上的其他處理序，就像目前處理序 \(MSHCTX\_LOCAL\) 。  
  
 `pvDestContext`  
 保留以備將來之用；必須為零。  
  
 `mshlflags`  
 指定要封送處理的資料是否要傳送回用戶端處理序—一般情況或被寫進全域資料表時，可由多個用戶端擷取。  
  
## 傳回值  
 S\_OK  
 介面指標成功封送處理。  
  
 E\_NOINTERFACE  
 不支援指定的型別。  
  
 STG\_E\_MEDIUMFULL  
 資料流已滿。  
  
 E\_FAIL  
 作業失敗。  
  
## 需求  
 **標題:** ftm.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)