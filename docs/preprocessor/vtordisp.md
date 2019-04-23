---
title: vtordisp
ms.date: 10/18/2018
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: 67c6c329bcee75012f6075334760925eca945501
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034374"
---
# <a name="vtordisp"></a>vtordisp

**C++特定**

加入隱藏 vtordisp 建構函式/解構函式替代成員的控制項。

## <a name="syntax"></a>語法

```cpp
#pragma vtordisp([push,] n)
#pragma vtordisp(pop)
#pragma vtordisp()
#pragma vtordisp([push,] {on | off})
```

### <a name="parameters"></a>參數

*push*<br/>
將目前的 vtordisp 設定推送內部編譯器堆疊上，並將新的 vtordisp 設定設為*n*。  如果*n*未指定，目前的 vtordisp 設定不會變更。

*pop*<br/>
從內部編譯器堆疊中移除最上方的記錄，並將 vtordisp 設定還原為已移除的值。

*n*<br/>
為 vtordisp 設定指定新的值。 可能的值為 0、 1 或 2，對應到`/vd0`， `/vd1`，和`/vd2`編譯器選項。 如需詳細資訊，請參閱 < [/vd （停用建構替代）](../build/reference/vd-disable-construction-displacements.md)。

*on*<br/>
相當於 `#pragma vtordisp(1)`。

*off*<br/>
相當於 `#pragma vtordisp(0)`。

## <a name="remarks"></a>備註

**Vtordisp** pragma 是只適用於使用虛擬基底的程式碼。 如果在衍生的類別覆寫虛擬函式，其繼承自虛擬的基底類別，而且如果建構函式或解構函式在衍生類別呼叫該函式使用虛擬基底類別指標，編譯器可能會造成額外的隱藏的**vtordisp**成具有虛擬基底類別的欄位。

**Vtordisp** pragma 會影響其後類別的配置。 `/vd0`， `/vd1`，和`/vd2`選項會指定完整模組相同的行為。 指定 0 或*關*會抑制隱藏**vtordisp**成員。 關閉**vtordisp**如果沒有不可能有的類別建構函式和解構函式呼叫虛擬函式所指向的物件上僅**這**指標。

指定 1 或*上*，預設值，可讓隱藏**vtordisp**他們所需的成員。

指定 2 啟用隱藏**vtordisp**具有虛擬函式的所有虛擬基底的成員。  `vtordisp(2)` 可能需要以確保正確的效能**dynamic_cast**在部分建構的物件。 如需詳細資訊，請參閱 <<c0> [ 編譯器警告 （層級 1） C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)。

`#pragma vtordisp()` (不含引數)，將 vtordisp 設定還原為其初始設定值。

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**結束C++特定**

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)