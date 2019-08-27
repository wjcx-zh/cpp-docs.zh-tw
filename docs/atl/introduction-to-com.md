---
title: COM 簡介
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: e29f761e0380357bc999af82cc4bde8bfbaf4d6e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492348"
---
# <a name="introduction-to-com"></a>COM 簡介

COM 是用來建立 ActiveX 控制項和 OLE 的基本「物件模型」。 COM 允許物件將其功能公開給其他元件, 並裝載應用程式。 它會定義物件本身的公開方式, 以及此公開在進程和網路之間的運作方式。 COM 也會定義物件的生命週期。

COM 的基本概念如下:

- [介面](../atl/interfaces-atl.md)-物件用來公開其功能的機制。

- [IUnknown](../atl/iunknown.md) —所有其他專案都是以其為基礎的基本介面。 它會實行透過 COM 執行的參考計數和介面查詢機制。

- [參考計數](../atl/reference-counting.md)-物件 (或嚴格的介面) 用來決定不再使用的技術, 因此可自由移除本身。

- [QueryInterface](../atl/queryinterface.md) -用來查詢給定介面之物件的方法。

- [封送處理](../atl/marshaling.md)—這種機制可讓您跨執行緒、進程和網路界限使用物件, 以允許位置獨立性。

- [匯總](../atl/aggregation.md)-一個物件可以利用另一個物件的方式。

## <a name="see-also"></a>另請參閱

[COM 和 ATL 簡介](../atl/introduction-to-com-and-atl.md)<br/>
[元件物件模型](/windows/win32/com/the-component-object-model)
