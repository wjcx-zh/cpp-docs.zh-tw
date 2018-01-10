---
title: "ATL 連接點範例 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf59a8093568b96b5f2173d91ba52a6bfeb103b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="atl-connection-point-example"></a>ATL 連接點範例
此範例顯示支援的物件[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)為外寄的介面：  
  
 [!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]  
  
 當指定`IPropertyNotifySink`為外寄的介面，您可以使用類別[IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)而不是`IConnectionPointImpl`。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]  
  
## <a name="see-also"></a>請參閱  
 [連接點](../atl/atl-connection-points.md)

