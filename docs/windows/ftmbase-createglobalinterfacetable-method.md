---
title: "FtmBase::CreateGlobalInterfaceTable 方法 | Microsoft Docs"
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
  - "ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateGlobalInterfaceTable 方法"
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::CreateGlobalInterfaceTable 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立全域介面表 \(GIT\)。  
  
## 語法  
  
```  
static HRESULT CreateGlobalInterfaceTable(  
   __out IGlobalInterfaceTable **git  
);  
```  
  
#### 參數  
 `git`  
 這個作業完成時，對全域資料表的介面指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，則為表示錯誤的 HRESULT。  
  
## 備註  
 如需詳細資訊，請參閱MSDN Library中「COM 參考」主題的子主題「COM 介面」中的的「IGlobalInterfaceTable」主題。  
  
## 需求  
 **標題:** ftm.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)