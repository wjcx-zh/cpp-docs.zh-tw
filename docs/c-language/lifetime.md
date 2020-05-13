---
title: 存留期
ms.date: 11/04/2016
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
ms.openlocfilehash: 962e5ef4cae1be142091d2a209b4c60c0b789e74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232770"
---
# <a name="lifetime"></a>存留期

「存留期」是有變數或函式的程式執行的期間。 識別項儲存期決定其存留期。

以 *storage-class-specifier* **static** 宣告的識別項會有靜態儲存期。 有靜態儲存期 (也稱為「全域」) 的識別項會儲存和定義代表程式期間的值。 在程式啟動前會保留儲存區，而且只會初始化一次識別項的儲存值。 以外部或內部連結宣告的識別項也會有靜態儲存期 (請參閱[連結](../c-language/linkage.md))。

識別項若是在函式中宣告，而且沒有以 **static** 儲存類別指定名稱進行宣告，則會有自動儲存期。 有自動儲存期的識別項 (「區域識別項」) 只會在定義或宣告該識別項的區塊中有儲存區和定義值。 每次程式進入該區塊時，就會為自動識別項配置新的儲存區，而且該自動識別項會在程式離開該區塊時失去其儲存區 (與其值)。 在函式中宣告且沒有連結的識別項也會有自動儲存期。

下列規則指定識別項具有全域 (靜態) 或區域 (自動) 存留期：

- 所有函式都具有靜態存留期。 因此，程式執行期間，所有函式始終存在。 在外部層級 (也就是在程式中所有與函式定義同層級之區塊以外) 宣告的識別項一律具有全域 (靜態) 存留期。

- 如果區域變數有初始設定式，就會在每次建立該變數時對它進行初始化 (除非它是以 **static** 宣告)。 函式參數也有區域存留期。 您可以透過在識別項的宣告中包含 **static** 儲存類別指定名稱，在區塊內為該識別項指定全域存留期。 一旦宣告 **static** 後，變數會在區塊的各個輸入項之間保留其值。

雖然具全域存留期的識別項在原始程式的整個執行期間 (例如外部宣告的變數或以 **static** 關鍵字宣告的區域變數) 都會存在，但可能不會出現在程式的所有部分。 如需可見度的相關資訊，請參閱[範圍和可見度](../c-language/scope-and-visibility.md)。如需 *storage-class-specifier* 非終端項的討論，請參閱[儲存類別](../c-language/c-storage-classes.md)。

如果是利用 `malloc` 之類的特殊程式庫常式建立記憶體，則可視需要 (動態) 配置記憶體。 因為動態記憶體配置使用程式庫常式，因此不被視為語言的一部分。 請參閱《執行階段程式庫參考》** 中的 [malloc](../c-runtime-library/reference/malloc.md) 函式。

## <a name="see-also"></a>請參閱

[存留期、範圍、可見度和連結](../c-language/lifetime-scope-visibility-and-linkage.md)
