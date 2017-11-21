---
title: "實作雙重介面 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b4895e7b1cd0e38b33c1efe66e9070073403ee01
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-a-dual-interface"></a>實作雙重介面
您可以實作雙重介面使用[IDispatchImpl](../atl/reference/idispatchimpl-class.md)類別，可提供的預設實作`IDispatch`雙重介面中的方法。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
 若要使用此類別：  
  
-   定義您的雙重介面類型程式庫中。  
  
-   衍生您的類別，從特製的`IDispatchImpl`（傳遞資訊相關的介面和類型程式庫當做範本引數）。  
  
-   加入項目 （或項目） 來公開透過雙重介面 COM 對應`QueryInterface`。  
  
-   在您類別中實作介面的 vtable 一部分。  
  
-   請確認包含介面定義的類型程式庫可對物件執行階段。  
  
## <a name="atl-simple-object-wizard"></a>ATL 簡單物件精靈  
 如果您想要建立新的介面和新的類別來實作它，您可以使用[ATL 加入類別對話方塊](../ide/add-class-dialog-box.md)，然後[ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)。  
  
## <a name="implement-interface-wizard"></a>實作介面精靈  
 如果您有現有的介面，您可以使用[實作介面精靈](../atl/reference/adding-a-new-interface-in-an-atl-project.md)將必要的基底類別、 COM 對應項目和基本架構的方法實作新增至現有的類別。  
  
> [!NOTE]
>  您可能需要調整所產生的基底類別，讓型別程式庫的主要和次要版本號碼會當做範本引數傳遞您`IDispatchImpl`基底類別。 實作介面精靈並不會檢查您的類型程式庫版本號碼。  
  
## <a name="implementing-idispatch"></a>實作 IDispatch  
 您可以使用`IDispatchImpl`基底類別，以提供的分配介面的實作，只要 COM 對應中指定適當的項目 (使用[COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)或[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid)巨集)，只要您有描述對應的雙重介面的型別程式庫。 若要實作相當常見`IDispatch`介面如此一來，例如。 ATL 簡單物件精靈] 及 [實作介面精靈同時假設您想要實作`IDispatch`如此一來，因此它們會加入適當的項目對應。  
  
> [!NOTE]
>  ATL 提供[IDispEventImpl](../atl/reference/idispeventimpl-class.md)和[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)類別可以幫助您實作分配介面，而不需要類型程式庫包含相容的雙重介面的定義。  
  
## <a name="see-also"></a>另請參閱  
 [雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)

