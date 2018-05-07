---
title: 實作介面精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.interface.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Interface Wizard [C++]
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf2ddf83b7a03f8d4e01b61f82e46e0d26a5547b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="implement-interface-wizard"></a>實作介面精靈
此精靈會實作 COM 物件的介面。 許多介面的實作會包含在 Visual Studio 和 Windows 中提供的 COM 程式庫。 時建立該物件的執行個體，並提供物件所提供的服務與物件相關聯的介面實作。  
  
 如需的介面和實作的討論，請參閱[介面及介面實作](http://msdn.microsoft.com/library/windows/desktop/ms694356)Windows SDK 中。  
  
 **從實作介面**  
 指定的位置建立該介面的類型程式庫。  
  
|選項|描述|  
|------------|-----------------|  
|**Project**|類型程式庫是專案的一部分。|  
|**Registry**|類型程式庫會在系統中註冊。 已註冊型別程式庫中所列**可用的型別程式庫**。|  
|**檔案**|類型程式庫不一定登錄在系統中，但是包含在檔案中。 您必須提供中的檔案位置**位置**。|  
  
 **可用的型別程式庫**  
 顯示可用的型別程式庫，其中包含您可以實作的介面定義。 如果您按一下**檔案**下**實作介面從**，此方塊，便無法變更。  
  
 **位置**  
 顯示的類型程式庫中目前選取位置**可用的型別程式庫**清單。 如果您選取**檔案**下**實作介面從**，按一下省略符號按鈕找出包含使用類型程式庫的檔案。  
  
 **介面**  
 顯示的介面的定義包含類型程式庫中目前選取**可用的型別程式庫**方塊。  
  
> [!NOTE]
>  因為已實作所選取的物件不會顯示在具有相同名稱的介面**介面**方塊。  
  
|傳送按鈕|描述|  
|---------------------|-----------------|  
|**>**|將加入至**實作介面**中目前選取的介面名稱**介面**清單。|  
|**>>**|將加入至**實作介面**清單中可用的所有介面名稱**介面**都清單。|  
|**<**|移除在目前選取的介面名稱**實作介面**清單。|  
|**<\<**|移除所有介面目前所列的名稱**實作介面**清單。|  
  
 **實作介面**  
 會顯示您已選取要在物件上實作的介面名稱。  
  
> [!NOTE]
>  如果您包含多個介面衍生自`IDispatch`，或者如果您嘗試實作的介面，衍生自另一個介面上您的類別，則您必須區分 COM_MAP 項目。 請參閱[COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [實作介面](../ide/implementing-an-interface-visual-cpp.md)