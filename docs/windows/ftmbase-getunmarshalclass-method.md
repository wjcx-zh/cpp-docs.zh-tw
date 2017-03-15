---
title: "FtmBase::GetUnmarshalClass 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetUnmarshalClass 方法"
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase::GetUnmarshalClass 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得 COM 來尋找包含對應之 Proxy 的 DLL 程式碼的 CLSID。  COM 載入此 DLL 建立 Proxy 的未初始化的執行個體。  
  
## 語法  
  
```  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
#### 參數  
 `riid`  
 要封送處理的介面識別項的參考。  
  
 `pv`  
 要封送處理介面的指標;如果呼叫端沒有所需的介面指標，則可為 NULL。  
  
 `dwDestContext`  
 指定的介面要解除封送處理目的端的內容。  
  
 指定一或多個 MSHCTX 列舉值。  
  
 Unmarshaling 可能發生在目前處理序 \(MSHCTX\_INPROC\) 的另一個 Apartment 或在電腦上其他處理序和目前處理序 \(MSHCTX\_LOCAL\) 相同。  
  
 `pvDestContext`  
 保留供日後使用，必須是 NULL。  
  
 `mshlflags`  
 這個作業完成時，會使用 CLSID 的指標會在用戶端處理序中的 Proxy。  
  
 `pCid`  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， S\_FALSE。  
  
## 需求  
 **標題:** ftm.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)