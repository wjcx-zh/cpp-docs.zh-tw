---
title: "ComPtr::CopyTo 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::CopyTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CopyTo 方法"
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::CopyTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

複製目前或指定介面與這個 ComPtr 至指定的指標。  
  
## 語法  
  
```  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  
template<  
   typename U  
>  
  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
#### 參數  
 `U`  
 型別名稱。  
  
 `ptr`  
 這個作業完成時，為所要求介面的指標。  
  
 `riid`  
 介面 ID。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， HRESULT 表示隱含 QueryInterface 作業失敗的原因。  
  
## 備註  
 第一個讓函式傳回指向與這個 ComPtr 相關的介面的指標的複本。  這個函式一定會傳回 S\_OK。  
  
 第二個函式會在介面的 QueryInterface 管理與 `riid` 參數所指定的介面執行 ComPtr。  
  
 第三個函式會為了 `U` 參數的底層介面對與這個 ComPtr 關連的介面執行 QueryInterface 作業。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ComPtr 類別](../windows/comptr-class.md)