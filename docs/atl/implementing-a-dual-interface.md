---
title: "Implementing a Dual Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "雙重介面, 實作"
  - "IDispatchImpl 類別, implementing dual interfaces"
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing a Dual Interface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 類別，您可以實作雙重介面，提供 `IDispatch` 方法的預設實作雙重介面的。  如需詳細資訊，請參閱 [Implementing the IDispatch Interface](http://msdn.microsoft.com/zh-tw/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
 使用這個類別:  
  
-   定義在型別程式庫中的雙重介面。  
  
-   從 `IDispatchImpl` 衍生您的類別 \(如需介面和型別程式庫的傳遞資訊的特製化做為樣板引數\)。  
  
-   在加入一個項目 \(或\) 輸入至 COM 對應傳遞 `QueryInterface`顯露雙重介面。  
  
-   實作介面的 vtable 部分類別中。  
  
-   確認型別包含介面定義的程式庫對物件也可以在執行階段。  
  
## ATL 簡單物件精靈  
 如果您想要建立新的介面和新類別實作時，您可以使用 [ATL 加入類別對話方塊。](../ide/add-class-dialog-box.md)然後 [ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)。  
  
## 實作介面精靈  
 如果您有現有的介面，您可以使用 [實作介面精靈](../atl/reference/adding-a-new-interface-in-an-atl-project.md) 加入必要的基底類別， COM 對應項目和最基本的方法實作加入至現有的類別。  
  
> [!NOTE]
>  您可能需要調整產生的基底類別，因此型別程式庫的主要和次要版本號碼傳遞做為樣板引數至 `IDispatchImpl` 基底類別。  實作介面精靈不會檢查型別程式庫版本號碼您。  
  
## 實作 IDispatch  
 您可以使用 `IDispatchImpl` 基底類別透過指定適當的項目提供分配介面的實作 COM 對應 \(使用 [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md) 或 [COM\_INTERFACE\_ENTRY\_IID](../Topic/COM_INTERFACE_ENTRY_IID.md) 巨集\)，只要您有型別描述對應的雙重介面 \(Dual Interface\) 的程式庫。  例如常常都的實作 `IDispatch` 介面，這類。  兩個假設的 ATL 簡單物件精靈和實作介面精靈，而您想要將這種實作， `IDispatch` ，這樣它們會將適當的項目加入至對應。  
  
> [!NOTE]
>  ATL 提供 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 和 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 類別可以協助您實作介面，而不需要型別包含適合雙重介面的定義的程式庫。  
  
## 請參閱  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)