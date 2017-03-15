---
title: "FtmBase::ReleaseMarshalData 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseMarshalData 方法"
ms.assetid: a94f9940-183a-4fde-8504-d223f346a0a9
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase::ReleaseMarshalData 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

摧毀封送處理的資料封包。  
  
## 語法  
  
```  
STDMETHODIMP ReleaseMarshalData(  
   __in IStream *pStm  
) override;  
```  
  
#### 參數  
 `pStm`  
 含有要終結的資料封包的資料流的指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，則為表示錯誤的 HRESULT。  
  
## 需求  
 **標題:** ftm.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)