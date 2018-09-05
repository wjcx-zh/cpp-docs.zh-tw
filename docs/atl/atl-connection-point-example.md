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
ms.openlocfilehash: b9aafd2676b1816737015b6af4fdbc9b3a710ae5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752354"
---
# <a name="atl-connection-point-example"></a>ATL 連接點範例

此範例會示範支援的物件[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)為外寄的介面：

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

指定時`IPropertyNotifySink`傳出的介面，您可以使用類別[IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)而不是`IConnectionPointImpl`。 例如: 

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>另請參閱

[連接點](../atl/atl-connection-points.md)

