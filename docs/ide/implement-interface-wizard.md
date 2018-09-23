---
title: 實作介面精靈 | Microsoft Docs
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
ms.openlocfilehash: 3e5d48688d271330c1cbcbac69f2e0b0c60ccbe8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713748"
---
# <a name="implement-interface-wizard"></a>實作介面精靈
這個精靈將實作 COM 物件的介面。 許多介面的實作會包含在 Visual Studio 和 Windows 所提供的 COM 程式庫中。 建立該物件的執行個體時，介面實作會與物件建立關聯，而且它會提供物件所提供的服務。  
  
如需介面和實作的討論，請參閱 Windows SDK 中的[介面和介面實作](/windows/desktop/com/interfaces-and-interface-implementations)。  
  
- **實作介面來源**

   指定從中建立介面之型別程式庫的位置。  
  
   |選項|描述|  
   |------------|-----------------|  
   |**Project**|型別程式庫是專案的一部分。|  
   |**Registry**|型別程式庫會在系統中註冊。 已註冊的型別程式庫會列於 [可用的型別程式庫] 中。|  
   |**檔案**|型別程式庫不一定會在系統中註冊，但會包含在檔案中。 您必須在 [位置] 中提供檔案位置。|  
  
- **可用的型別程式庫**

   顯示可用的型別程式庫，其中包含您可以實作的介面定義。 如果您在 [實作介面來源] 下按一下 [檔案]，此方塊無法用於變更。  
  
- **位置**

   顯示 [可用的型別程式庫] 清單中目前選取之型別程式庫的位置。 如果您選取 [實作介面來源] 下的 [檔案]，請按一下省略符號按鈕，以找出包含要使用之型別程式庫的檔案。  
  
- **介面**

   顯示其定義包含在 [可用的型別程式庫] 方塊中目前選取之型別程式庫中的介面。  
  
   > [!NOTE]
   > 與已由選取的物件所實作之介面同名的介面不會顯示在 [介面] 方塊中。  
  
   |傳輸按鈕|描述|  
   |---------------------|-----------------|  
   |**>**|將 [介面] 清單中目前選取的介面名稱新增至 [實作介面] 清單。|  
   |**>>**|將 [介面] 清單中所有可用介面名稱新增至 [實作介面] 清單。|  
   |**\<**|移除 [實作介面] 清單中目前選取的介面名稱。|  
   |**\<\<**|移除 [實作介面] 清單中目前列出的所有介面名稱。|  
  
- **實作介面**

   顯示您已選取要在物件上實作的介面名稱。  
  
   > [!NOTE]
   > 如果您包含多個衍生自 `IDispatch` 的介面，或者如果嘗試實作衍生自類別之另一個介面的介面，則您必須區分 COM_MAP 項目。 請參閱 [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2) 以取得詳細資訊。  
  
## <a name="see-also"></a>請參閱  
 [實作介面](../ide/implementing-an-interface-visual-cpp.md)