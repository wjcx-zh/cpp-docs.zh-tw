---
title: 建立彙總的物件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35ddbd6b8db853967a70de0427cc842689d55c82
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355016"
---
# <a name="creating-an-aggregated-object"></a>建立彙總的物件
彙總委派**IUnknown**呼叫，提供在外部物件的指標**IUnknown**內部物件。  
  
### <a name="to-create-an-aggregated-object"></a>若要建立彙總的物件  
  
1.  新增**IUnknown**指向您的類別物件，並將它初始化來**NULL**建構函式中。  
  
2.  覆寫[跖](../atl/reference/ccomobjectrootex-class.md#finalconstruct)來建立彙總。  
  
3.  使用**IUnknown**指標，在步驟 1 中定義的第二個參數為[COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate)巨集。  
  
4.  覆寫[FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease)釋放**IUnknown**指標。  
  
> [!NOTE]
>  如果您使用並發行期間的彙總物件的介面`FinalConstruct`，您應該加入[DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct)類別物件定義的巨集。  
  
## <a name="see-also"></a>另請參閱  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)

