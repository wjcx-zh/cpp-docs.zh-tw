---
title: "建立彙總的物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b6b66a80c5459157b644ec6b264b707232c83e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)

