---
title: 讓 ATL 物件變成無法建立
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: b2d0a21ec9e68f76650f0f6cb78446bd93540fa2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506956"
---
# <a name="making-an-atl-object-noncreatable"></a>讓 ATL 物件變成無法建立

您可以變更 ATL COM 物件的屬性，讓用戶端無法直接建立物件。 在此情況下，物件會透過另一個物件上的方法呼叫傳回，而不是直接建立。

## <a name="to-make-an-object-noncreatable"></a>若要讓物件 noncreatable

1. 移除物件的 [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) 。 如果您想要 noncreatable 物件，但要註冊控制項，請將 OBJECT_ENTRY_AUTO 取代為 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)。

1. 將 [noncreatable](../../windows/attributes/noncreatable.md) 屬性新增至 .idl 檔案中的 coclass。 例如：

    ```
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),
    helpstring("MyObject"),
    noncreatable]
    coclass MyObject
    {
        [default] interface IMyInterface;
    }
    ```

## <a name="see-also"></a>另請參閱

[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio 中的 C++ 專案類型](../../build/reference/visual-cpp-project-types.md)<br/>
[使用 ATL 和 C 執行時間程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[預設 ATL 專案設定](../../atl/reference/default-atl-project-configurations.md)
