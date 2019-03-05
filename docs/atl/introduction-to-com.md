---
title: COM 簡介
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: 7631ba98b0e2cb00310400206b0b442ab7a23dd7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277426"
---
# <a name="introduction-to-com"></a>COM 簡介

COM 是基本 「 物件模型 」 上的 ActiveX 控制項和 OLE 會建置。 COM 可讓物件公開給其他元件和主控件應用程式，其功能。 它會定義物件如何公開本身和跨處理序和跨網路，此公開資訊的運作方式。 COM 也會定義物件的生命週期。

COM 的基礎是這些概念：

- [介面](../atl/interfaces-atl.md)— 透過此物件會公開其功能的機制。

- [IUnknown](../atl/iunknown.md) — 所有其他人所依據的基本介面。 它會實作參考計數和查詢機制執行透過 COM 介面

- [參考計數](../atl/reference-counting.md)— 由此物件 （或嚴格來說，介面） 會決定當它已不再使用，因此可以移除本身的技術。

- [QueryInterface](../atl/queryinterface.md) — 用來查詢物件的指定介面的方法。

- [封送處理](../atl/marshaling.md)— 可讓物件以在各種不同的執行緒、 流程和網路界限，讓位置獨立性的機制。

- [彙總](../atl/aggregation.md)— 的方法在其中一個物件可以使用另一個。

## <a name="see-also"></a>另請參閱

[COM 和 ATL 簡介](../atl/introduction-to-com-and-atl.md)<br/>
[元件物件模型](/windows/desktop/com/the-component-object-model)
