---
title: "FtmBase::GetMarshalSizeMax 方法 | Microsoft Docs"
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
  - "ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMarshalSizeMax 方法"
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::GetMarshalSizeMax 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得所需的位元組數目的上限 \(Upper Bound\) 封送處理指定的物件的指定介面的指標。  
  
## 語法  
  
```  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
#### 參數  
 `riid`  
 要封送處理的介面識別項的參考。  
  
 `pv`  
 要封送處理的介面指標;可以是空白。  
  
 `dwDestContext`  
 要解除指定介面封送處理的目的端內容。  
  
 指定一或多個 MSHCTX 列舉值。  
  
 目前，Unmarshaling 可能發生在目前處理序 \(MSHCTX\_INPROC\) 的另一個 Apartment 或在同一台電腦上和目前處理序 \(MSHCTX\_LOCAL\) 相同的其他處理序。  
  
 `pvDestContext`  
 保留供日後使用，必須是 NULL。  
  
 `mshlflags`  
 旗標表示封送處理的資料是否要傳送回用戶端處理序—一般情況或重新命名全域資料表時，可由多個用戶端擷取。  指定一或多個 MSHCTX 列舉值。  
  
 `pSize`  
 這個作業完成時，指向要寫入封送處理資料流資料的上限的指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， E\_NOINTERFACE 或 E\_FAIL。  
  
## 需求  
 **標題:** ftm.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)