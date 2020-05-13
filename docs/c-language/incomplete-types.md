---
title: 不完整的類型
ms.date: 11/04/2016
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
ms.openlocfilehash: e7a5cd7624b55e7bce0fbd09451ab42426f5bc37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232888"
---
# <a name="incomplete-types"></a>不完整的類型

「*不完整的類型*」是一種描述識別碼的類型，但缺少判斷識別碼大小所需的資訊。 「不完整類型」可以是：

- 您尚未指定成員的結構類型。

- 您尚未指定成員的等位類型。

- 您尚未指定維度的陣列類型。

**Void**類型是無法完成的不完整類型。 若要完成不完整類型，請指定遺漏的資訊。 下列範例顯示如何建立和完成不完整類型。

- 若要建立不完整的結構類型，請宣告一個結構類型，但不指定其成員。 在此範例中，`ps` 指標會指向名為 `student` 的不完整結構類型。

    ```C
    struct student *ps;
    ```

- 若要完成不完整的結構類型，請於稍後使用其指定的成員在相同範圍中宣告相同的結構類型，如下所示

    ```C
    struct student
    {
        int num;
    }                   /* student structure now completed */
    ```

- 若要建立不完整的陣列類型，請宣告一個陣列類型，而不指定其重複計數。 例如：

    ```C
    char a[];  /* a has incomplete type */
    ```

- 若要完成不完整的陣列類型，請於稍後使用其指定的重複計數在相同範圍中宣告相同的名稱，如下所示

    ```C
    char a[25]; /* a now has complete type */
    ```

## <a name="see-also"></a>請參閱

[宣告和類型](../c-language/declarations-and-types.md)
