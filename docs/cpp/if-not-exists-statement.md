---
title: __if_not_exists 陳述式
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 845597460cdc0ce83adcbba1f47a78c83735cbf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183631"
---
# <a name="ifnotexists-statement"></a>__if_not_exists 陳述式

**__If_not_exists**陳述式會測試是否存在指定的識別項。 如果識別項不存在，就會執行指定的陳述式區塊。

## <a name="syntax"></a>語法

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*identifier*|要測試其是否存在的識別項。|
|*statements*|若要執行的一或多個陳述式*識別碼*不存在。|

## <a name="remarks"></a>備註

> [!CAUTION]
>  若要達到最可靠的結果，使用 **__if_not_exists**低於下列條件約束陳述式。

- 適用於 **__if_not_exists**只是簡單類型，而不是範本的陳述式。

- 適用於 **__if_not_exists**類別內外的識別項的陳述式。 不適用 **__if_not_exists**至區域變數的陳述式。

- 使用 **__if_not_exists**只能在函式主體中的陳述式。 函式的主體的外面 **__if_not_exists**完整定義的類型只能測試陳述式。

- 當您對多載函式進行測試時，無法對特定形式的多載進行測試。

若要補充 **__if_not_exists**陳述式是[__if_exists](../cpp/if-exists-statement.md)陳述式。

## <a name="example"></a>範例

如需有關如何使用範例 **__if_not_exists**，請參閱[__if_exists 陳述式](../cpp/if-exists-statement.md)。

## <a name="see-also"></a>另請參閱

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[__if_exists 陳述式](../cpp/if-exists-statement.md)