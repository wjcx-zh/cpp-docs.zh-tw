---
title: "FtmBase::UnmarshalInterface 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::UnmarshalInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UnmarshalInterface 方法"
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase::UnmarshalInterface 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化新建立的 Proxy 並傳回介面指標該 Proxy。  
  
## 語法  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### 參數  
 `pStm`  
 對介面指標要解除封送處理資料流的指標。  
  
 `riid`  
 要解除封送處理的介面識別項的參考。  
  
 `ppv`  
 當這個作業完成時，會接收在 `riid`要求的介面指標變數的位址。  如果作業成功， \*`ppv` 包含解除封送處理的介面之要求的介面指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， E\_NOINTERFACE 或 E\_FAIL。  
  
## 需求  
 **標題:** ftm.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)