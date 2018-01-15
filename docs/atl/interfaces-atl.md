---
title: "介面 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf1dd68a3ca8e6735b07c5bd7247b457bd7d246d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="interfaces-atl"></a>介面 (ATL)
介面是物件會公開其功能給外界的方式。 在 COM 中，介面是由物件所實作的函式的指標 （例如 c + + vtable) 的資料表。 資料表代表介面，以及它所指向的功能是該介面的方法。 物件可以公開其選擇的介面。  
  
 每個介面為基礎的基本的 COM 介面， [IUnknown](../atl/iunknown.md)。 方法的**IUnknown**可瀏覽其他物件所公開的介面。  
  
 此外，每個介面會提供唯一的介面識別碼 (IID)。 這個唯一性輕鬆地支援介面版本設定。 新版是介面的只是介面的新的介面，新的 iid。  
  
> [!NOTE]
>  預先定義的標準 COM 和 OLE 介面的 Iid。  
  
## <a name="see-also"></a>請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [COM 物件與介面](http://msdn.microsoft.com/library/windows/desktop/ms690343)

