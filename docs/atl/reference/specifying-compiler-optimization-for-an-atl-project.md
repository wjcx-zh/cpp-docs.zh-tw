---
title: 指定 ATL 專案的編譯器最佳化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
dev_langs:
- C++
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 622c0720f55e638d6640094f095e59d2d5e5f931
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069335"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>指定 ATL 專案的編譯器最佳化

根據預設， [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)產生 ATL_NO_VTABLE 巨集的新類別，如下所示：

```
class ATL_NO_VTABLE CProjName
{
...
};
```

ATL 然後 _ATL_NO_VTABLE 會，如下所示的定義：

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

如果您沒有定義 _ATL_DISABLE_NO_VTABLE，ATL_NO_VTABLE 巨集會展開`declspec(novtable)`。 使用`declspec(novtable)`類別中宣告可防止 vtable 指標在類別建構函式和解構函式中初始化。 當您建置專案時，連結器會消除 vtable 和 vtable 所指向的所有函式。

您必須使用 ATL_NO_VTABLE，並進而`declspec(novtable)`，不是直接可建立只基底的類別。 您不能使用`declspec(novtable)`與最高衍生性類別，在您的專案，因為這個類別 (通常[CComObject](../../atl/reference/ccomobject-class.md)， [CComAggObject](../../atl/reference/ccomaggobject-class.md)，或[CComPolyObject](../../atl/reference/ccompolyobject-class.md))vtable 指標初始化為您的專案。

您必須從使用的任何物件的建構函式呼叫虛擬函式`declspec(novtable)`。 您應該將這些呼叫移[跖](ccomobjectrootex-class.md#finalconstruct)方法。  

如果您不確定您是否應使用`declspec(novtable)`修飾詞，您可以從任何類別定義，移除 ATL_NO_VTABLE 巨集，或您可以全域停用它藉由指定

```
#define _ATL_DISABLE_NO_VTABLE
```

在 stdafx.h 中之前的所有其他 ATL 標頭檔會包含。

## <a name="see-also"></a>另請參閱

[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)<br/>
[Visual C++ 專案類型](../../ide/visual-cpp-project-types.md)<br/>
[使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)

