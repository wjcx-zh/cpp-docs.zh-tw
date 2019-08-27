---
title: 指定 ATL 專案的編譯器優化
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: c3b00823cb33be952451c3cc9e370c99140acc3c
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630618"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>指定 ATL 專案的編譯器優化

根據預設, [ATL 控制項嚮導](../../atl/reference/atl-control-wizard.md)會使用 ATL_NO_VTABLE 宏來產生新的類別, 如下所示:

```
class ATL_NO_VTABLE CProjName
{
...
};
```

然後 ATL 會定義 _ATL_NO_VTABLE, 如下所示:

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

如果您未定義 _ATL_DISABLE_NO_VTABLE, ATL_NO_VTABLE 宏會展開為`declspec(novtable)`。 在`declspec(novtable)`類別宣告中使用, 可防止 vtable 指標在類別的函式和析構函數中初始化。 當您建立專案時, 連結器會排除 vtable 和 vtable 所指向的所有函式。

您必須使用 ATL_NO_VTABLE, 因此`declspec(novtable)`, 只有不是直接可供您使用的基類。 您不能在`declspec(novtable)`專案中使用與最常衍生的類別, 因為這個類別 (通常是[CComObject](../../atl/reference/ccomobject-class.md)、 [CComAggObject](../../atl/reference/ccomaggobject-class.md)或[CComPolyObject](../../atl/reference/ccompolyobject-class.md)) 會初始化專案的 vtable 指標。

您不能從任何使用`declspec(novtable)`之物件的函式中呼叫虛擬函式。 您應該將這些呼叫移至[FinalConstruct](ccomobjectrootex-class.md#finalconstruct)方法。

如果您不確定是否應該使用`declspec(novtable)`修飾詞, 則可以從任何類別定義中移除 ATL_NO_VTABLE 宏, 也可以藉由指定來全域停用它

```
#define _ATL_DISABLE_NO_VTABLE
```

在*pch*中 (Visual Studio 2017 和更早版本中的*stdafx.h* ), 在包含所有其他 ATL 標頭檔之前。

## <a name="see-also"></a>另請參閱

[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio 中的 C++ 專案類型](../../build/reference/visual-cpp-project-types.md)<br/>
[使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)
