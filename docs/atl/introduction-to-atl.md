---
title: ATL 簡介
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM objects, creating in ATL
- ATL
ms.assetid: 77f565e8-c4ec-4a80-af4b-7278fcfe5c98
ms.openlocfilehash: 8c2dcab962cd9863acf0f8e7070727f3b18117d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261913"
---
# <a name="introduction-to-atl"></a>ATL 簡介

ATL 的 Active Template Library 的範本為基礎的一組C++類別，您可以使用它輕鬆建立小型、 快速元件物件模型 (COM) 物件。 它有索引鍵的 COM 功能，包括特殊支援： 內建的實作[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)， [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)， [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)，和`IDispatch`雙重;介面，標準的 COM 列舉程式介面;連接點;tear-off 介面;和 ActiveX 控制項。

ATL 程式碼可用來建立單一執行緒物件、 apartment 模型物件、 無限制執行緒模型物件或無限制執行緒和 apartment model 物件。

本章節涵蓋的主題包括：

- 如何[範本庫](../atl/using-a-template-library.md)不同於標準程式庫。

- 你[可以和無法使用 ATL](../atl/scope-of-atl.md)。

- [ATL 和 MFC 之間選擇的建議](../atl/recommendations-for-choosing-between-atl-and-mfc.md)。

## <a name="see-also"></a>另請參閱

[COM 和 ATL 簡介](../atl/introduction-to-com-and-atl.md)
