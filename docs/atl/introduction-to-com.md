---
title: COM 簡介 |Microsoft 文件
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 938d0c45cae5ec9a2988f77f539af1a3d5513b83
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356171"
---
# <a name="introduction-to-com"></a>COM 簡介
COM 是基本 「 物件模型 」 上的 ActiveX 控制項和 OLE 已內建。 COM，允許物件來公開其功能給其他元件和主控件應用程式。 它會定義如何物件會公開本身和跨處理序和跨網路，此公開資訊的運作方式。 COM 也會定義物件的生命週期。  
  
 COM 的基礎是這些概念：  
  
-   [介面](../atl/interfaces-atl.md)— 透過此物件會公開其功能的機制。  
  
-   [IUnknown](../atl/iunknown.md) -其他所有項目所根據的基本介面。 它會實作的參考計數和查詢機制執行透過 COM 介面  
  
-   [參考計數](../atl/reference-counting.md)— 之物件 （或嚴格來說，介面） 會決定當它不再使用，因此可用來移除本身的技巧。  
  
-   [QueryInterface](../atl/queryinterface.md) — 用來查詢物件的指定介面的方法。  
  
-   [封送處理](../atl/marshaling.md)— 可讓物件來跨執行緒、 處理程序和網路界限時，允許使用位置的獨立性的機制。  
  
-   [彙總](../atl/aggregation.md)— 可以在一個物件的方式使用另一個。  
  
## <a name="see-also"></a>另請參閱  
 [COM 和 ATL 簡介](../atl/introduction-to-com-and-atl.md)   
 [元件物件模型](http://msdn.microsoft.com/library/windows/desktop/ms694363)

