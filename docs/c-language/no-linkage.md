---
title: 無連結
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: a7c9a5b8f0ba92830500e55818093981a044d2df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218802"
---
# <a name="no-linkage"></a>無連結

如果區塊內識別碼的宣告不包含 **`extern`** 儲存類別規範，則識別碼不會有連結，而且對函式而言是唯一的。

下列識別項不會進行連結：

- 除了物件或函式之外，可項識別項宣告為任何項目

- 宣告為函式參數的識別項

- 未使用 **`extern`** 儲存類別規範宣告之物件的區塊範圍識別碼

如果識別項未連結，則在相同範圍層級中再次宣告相同名稱 (在宣告子或類型指定名稱中) 會產生符號重新定義錯誤。

## <a name="see-also"></a>另請參閱

[使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)
