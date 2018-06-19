---
title: 介面 (ATL) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0db5a79f187cb0fe320bf67aace751a5d4c537d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359310"
---
# <a name="interfaces-atl"></a>介面 (ATL)
介面是物件會公開其功能給外界的方式。 在 COM 中，介面是由物件所實作的函式的指標 （例如 c + + vtable) 的資料表。 資料表代表介面，以及它所指向的功能是該介面的方法。 物件可以公開其選擇的介面。  
  
 每個介面為基礎的基本的 COM 介面， [IUnknown](../atl/iunknown.md)。 方法的**IUnknown**可瀏覽其他物件所公開的介面。  
  
 此外，每個介面會提供唯一的介面識別碼 (IID)。 這個唯一性輕鬆地支援介面版本設定。 新版是介面的只是介面的新的介面，新的 iid。  
  
> [!NOTE]
>  預先定義的標準 COM 和 OLE 介面的 Iid。  
  
## <a name="see-also"></a>另請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [COM 物件與介面](http://msdn.microsoft.com/library/windows/desktop/ms690343)

