---
title: 使用包含的視窗
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 5da765eae28d411c98e79af5b9173f48ea66ef8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329311"
---
# <a name="using-contained-windows"></a>使用包含的視窗

ATL 以包含包含[C 包含視窗視窗 。](../atl/reference/ccontainedwindowt-class.md) 包含的視窗表示一個視窗,該視窗將其消息委託給容器物件,而不是在自己的類中處理它們。

> [!NOTE]
> 不需要派生`CContainedWindowT`類,以便使用包含的視窗。

使用包含的視窗,可以超類現有 Windows 類或子類現有視窗。 要創建一個將現有 Windows 類類類超級類的視窗,請`CContainedWindowT`先在 物件的構造函數中指定現有類名稱。 然後呼叫`CContainedWindowT::Create`。 要對現有視窗進行子類設置,不需要指定 Windows 類名稱(將 NULL 傳遞給構造函數)。 只需調用`CContainedWindowT::SubclassWindow`方法,對正在下類的視窗的句柄進行調用。

通常使用包含的視窗作為容器類的數據成員。 容器不需要是視窗;因此,容器不需要是視窗。但是,它必須派生自[CMessageMap](../atl/reference/cmessagemap-class.md)。

包含的視窗可以使用備用消息映射來處理其消息。 如果有多個包含的視窗,則應聲明多個備用消息映射,每個映射對應於一個單獨的包含視窗。

## <a name="example"></a>範例

下面是包含兩個包含視窗的容器類的範例:

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

有關包含的視窗的詳細資訊,請參閱[SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)範例。

## <a name="see-also"></a>另請參閱

[視窗類](../atl/atl-window-classes.md)
