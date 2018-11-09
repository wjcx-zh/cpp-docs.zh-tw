---
title: C 儲存類別
ms.date: 08/31/2018
helpviewer_keywords:
- static variables, lifetime
- storage classes
- lifetime, variables
- specifiers, storage class
- storage class specifiers, C storage classes
- storage duration
ms.assetid: 893fb929-f7a9-43dc-a0b3-29cb1ef845c1
ms.openlocfilehash: cb472ea0db67e0fd8d7f2a8e2af4513ffb0fbe1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466179"
---
# <a name="c-storage-classes"></a>C 儲存類別

變數的「儲存類別」可判斷項目的存留期為「全域」或「區域」。 C 將這兩個存留期稱為「靜態」和「自動」。 具有全域存留期的項目會持續存在，並且在程式的整個執行過程中保有值。 所有函式都具有全域存留期。

每次當有控制項傳遞至用於定義自動變數，或具有區域存留期之變數的區塊時，就會為這些變數配置新的儲存區。 當執行回傳時，變數就不再包含有意義的值。

C 提供了下列儲存類別指定名稱：

## <a name="syntax"></a>語法

*storage-class-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**自動**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**註冊**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**靜態**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**外部**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl-modifier-seq* **)** /\* Microsoft 專有 \*/

除了 `__declspec` 之外，您只能在宣告的 *declaration-specifier* 中使用一個 *storage-class-specifier*。 如果未指定儲存類別，則區塊內的宣告會建立自動物件。

以 **auto** 或 **register** 指定名稱宣告的項目具有區域存留期。 以 **static** 或 `extern` 指定名稱宣告的項目則具有全域存留期。

由於 `typedef` 與 `__declspec` 在語意上與其他四個 *storage-class-specifier* 終端項不同，因此我們會分別討論它們。 如需有關 `typedef` 的特定資訊，請參閱 [Typedef 宣告](../c-language/typedef-declarations.md)。 如需有關 `__declspec` 的特定資訊，請參閱[擴充儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)。

變數和函式宣告在原始程式檔內的位置也會影響儲存類別和可視性。 在所有函式定義外部的宣告會稱為出現在「外部層級」。 在函式定義內的宣告則出現在「內部層級」。

每一個儲存類別指定名稱的確切意義取決於兩個因素：

- 宣告出現在外部或內部層級

- 所要宣告的項目為變數或函式

[外部層級宣告的儲存類別指定名稱](../c-language/storage-class-specifiers-for-external-level-declarations.md)和[內部層級宣告的儲存類別指定名稱](../c-language/storage-class-specifiers-for-internal-level-declarations.md)將描述各種宣告中的 *storage-class-specifier* 終端項，並且說明變數中省略 *storage-class-specifier* 時的預設行為。 [具有函式宣告的儲存類別指定名稱](../c-language/storage-class-specifiers-with-function-declarations.md)將討論搭配函式使用的儲存類別指定名稱。

## <a name="see-also"></a>請參閱

[宣告和類型](../c-language/declarations-and-types.md)
