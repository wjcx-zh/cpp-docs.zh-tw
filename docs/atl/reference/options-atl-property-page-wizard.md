---
title: "選項、 ATL 屬性頁面精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.ppg.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: bea768cf456fadfbe05e450c5e6652d1f7f378f5
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="options-atl-property-page-wizard"></a>選項, ATL 屬性頁精靈
使用精靈的這個頁面來定義您要建立屬性頁的執行緒模型和彙總層級。  
  
 **執行緒模型**  
 指定屬性頁面所使用的執行緒模型。  
  
 請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)如需詳細資訊。  
  
|選項|說明|  
|------------|-----------------|  
|`Single`|[屬性] 頁面上只會在執行主要的 COM 執行緒。|  
|**Apartment**|可以在任何單一執行緒 apartment 中建立屬性頁。 預設值。|  
  
 **彙總**  
 加入彙總支援您所建立的屬性頁。 請參閱[彙總](../../atl/aggregation.md)如需詳細資訊。  
  
|選項|說明|  
|------------|-----------------|  
|**[是]**|建立可彙總的屬性頁面。|  
|**No**|建立無法彙總的屬性頁面。|  
|**只有**|建立只能透過彙總執行個體化的屬性頁面。|  
  
## <a name="see-also"></a>另請參閱  
 [ATL 屬性頁面精靈](../../atl/reference/atl-property-page-wizard.md)   
 [字串，ATL 屬性頁面精靈](../../atl/reference/strings-atl-property-page-wizard.md)


