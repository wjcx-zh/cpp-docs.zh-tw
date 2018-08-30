---
title: ATL 連接點範例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a35b1e40718c26eb094eddb420f885a37907071
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212590"
---
# <a name="atl-connection-point-example"></a>ATL 連接點範例
此範例會示範支援的物件[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)為外寄的介面：  
  
 [!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]  
  
 指定時`IPropertyNotifySink`傳出的介面，您可以使用類別[IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)而不是`IConnectionPointImpl`。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]  
  
## <a name="see-also"></a>另請參閱  
 [連接點](../atl/atl-connection-points.md)

