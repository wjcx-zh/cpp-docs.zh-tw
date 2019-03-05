---
title: 使用包含的 Windows
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 2b9a36c6aac80a7c77cde102d6da93c51788e4e1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295145"
---
# <a name="using-contained-windows"></a>使用包含的 Windows

ATL 實作使用自主的視窗[CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)。 包含的視窗表示委派 (delegate) 給容器物件，而不是在它自己的類別中處理這些訊息的視窗。

> [!NOTE]
>  您不需要衍生類別，以從`CContainedWindowT`若要使用自主的視窗。

使用自主視窗，您可以是超級類別，現有的 Windows 類別或子類別化現有視窗。 若要建立視窗，是現有的 Windows 類別中，先將現有的類別名稱指定的建構函式`CContainedWindowT`物件。 然後呼叫`CContainedWindowT::Create`。 子類別化現有視窗，您不需要指定 Windows 的類別名稱 （建構函式傳遞 NULL）。 只要呼叫`CContainedWindowT::SubclassWindow`方法正在子類別化視窗的控制代碼。

通常，您會使用自主的視窗做為資料成員的容器類別。 容器不需要是視窗;不過，它必須衍生自[CMessageMap](../atl/reference/cmessagemap-class.md)。

包含的視窗可以使用替代的訊息對應來處理其訊息。 如果您有多個包含的視窗，您應該宣告多個替代訊息對應，各有一個對應至個別的自主視窗。

## <a name="example"></a>範例

以下是兩個包含的 windows 容器類別的範例：

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

如需有關自主視窗的詳細資訊，請參閱[SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)範例。

## <a name="see-also"></a>另請參閱

[視窗類別](../atl/atl-window-classes.md)
