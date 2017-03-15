---
title: "FtmBase 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FtmBase 類別"
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示無限制執行緒封送處理器物件。  
  
## 語法  
  
```  
  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags< WinRtClassicComMix >,   
   Microsoft::WRL::CloakedIid< IMarshal > >;  
```  
  
## 備註  
 如需詳細資訊，請參閱中「COM MSDN Library 中的連接」COM 參考\>主題的子主題的「IMarshal \>主題。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[FtmBase::FtmBase 建構函式](../windows/ftmbase-ftmbase-constructor.md)|初始化 FtmBase 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[FtmBase::CreateGlobalInterfaceTable 方法](../windows/ftmbase-createglobalinterfacetable-method.md)|建立全域介面表 \(GIT\)。|  
|[FtmBase::DisconnectObject 方法](../windows/ftmbase-disconnectobject-method.md)|強制釋放物件的所有外部連接。  物件的伺服器在關閉之前呼叫這個方法之物件的實作。|  
|[FtmBase::GetMarshalSizeMax 方法](../windows/ftmbase-getmarshalsizemax-method.md)|取得所需的位元組數目的上限 \(Upper Bound\) 封送處理指定的物件的指定介面的指標。|  
|[FtmBase::GetUnmarshalClass 方法](../windows/ftmbase-getunmarshalclass-method.md)|取得 COM 來尋找包含對應之 Proxy 的 DLL 程式碼的 CLSID。  COM 載入此 DLL 建立 Proxy 的未初始化的執行個體。|  
|[FtmBase::MarshalInterface 方法](../windows/ftmbase-marshalinterface-method.md)|寫入至資料流中所要求的資料初始化某個用戶端處理序中的 Proxy 物件。|  
|[FtmBase::ReleaseMarshalData 方法](../windows/ftmbase-releasemarshaldata-method.md)|摧毀封送處理的資料封包。|  
|[FtmBase::UnmarshalInterface 方法](../windows/ftmbase-unmarshalinterface-method.md)|初始化新建立的 Proxy 並傳回介面指標該 Proxy。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[FtmBase::marshaller\_ 資料成員](../windows/ftmbase-marshaller-data-member.md)|保留無限制執行緒封送處理器的參考。|  
  
## 繼承階層架構  
 `FtmBase`  
  
## 需求  
 **標題:** ftm.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)