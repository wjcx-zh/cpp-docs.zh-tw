---
title: "ATL 和無限制執行緒封送處理器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 無限制執行緒封送處理器"
  - "無限制執行緒封送處理器"
  - "ATL 中的 FTM"
  - "執行緒 [ATL], 無限制執行緒封送處理器"
  - "執行緒 [C++], ATL 中的封送處理器"
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ATL 和無限制執行緒封送處理器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 簡單物件精靈的屬性頁會提供讓類別彙總 \(Aggregate\) 無限制執行緒封送處理器 \(FTM\) 的選項。  
  
 精靈產生的程式碼建立無限制執行緒封送處理器的執行個體。 `FinalConstruct` 的及解除鎖定 `FinalRelease`的執行個體。  `COM_INTERFACE_ENTRY_AGGREGATE` 巨集會自動加入至 COM 對應確保 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707) 的 `QueryInterface` 要求無限制執行緒封送處理器處理。  
  
 無限制執行緒封送處理器允許存取介面的直接存取中的所有執行緒的物件在相同的處理序，加速跨 Apartment 呼叫。  這個選項適用的兩個執行緒模型的類別。  
  
 在使用選項時，類別必須負責其資料執行緒安全性的責任。  此外，針對彙總無限制執行緒封送處理器和需要使用衍生自其他物件的介面指標必須採取其他步驟以確保介面正確封送處理。  通常，每次使用，這需要儲存介面指標在全域介面表 \(GIT\) 中並取得指標從 GIT 它。  提供 ATL 類別 [CComGITPtr](../atl/reference/ccomgitptr-class.md) 可協助您在 GIT 儲存的介面指標。  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [When to Use the Global Interface Table](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [In\-Process Server Threading Issues](http://msdn.microsoft.com/library/windows/desktop/ms687205)