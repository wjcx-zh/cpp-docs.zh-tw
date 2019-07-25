---
title: 輸出資料流
ms.date: 11/04/2016
helpviewer_keywords:
- output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
ms.openlocfilehash: e650f9fd0bbc7ad483363706e632686e8ec3749e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450165"
---
# <a name="output-streams"></a>輸出資料流

輸出資料流物件是位元組的目的地。 三種最重要的輸出資料流類別為：`ostream`、`ofstream` 和 `ostringstream`。

`ostream` 類別，透過衍生的類別 `basic_ostream`，支援預先定義的資料流物件：

- `cout` 標準輸出

- `cerr` 具有有限緩衝的標準錯誤

- `clog` 類似於 `cerr`，但具有完整緩衝

物件很少從 `ostream` 建構；通常會使用預先定義的物件。 在某些情況下，您可以在程式啟動之後重新指派預先定義的物件。 `ostream` 類別 (可針對經緩衝或未經緩衝的作業設定) 最適合循序文字模式輸出。 基底類別 `ios` 的所有功能都包含在 `ostream` 中。 如果您建構 `ostream` 類別的物件，您必須對建構函式指定 `streambuf` 物件。

`ofstream` 類別支援磁碟檔案輸出。 如果您需要輸出專用磁碟，請建構 `ofstream` 類別的物件。 建構 `ofstream` 物件或是呼叫物件的 `open` 成員函式時，您可以指定 `ofstream` 物件要接受二進位或文字模式資料。 許多格式選項和成員函式適用於 `ofstream` 物件，而且包含基底類別 `ios` 和 `ostream` 的所有功能。

如果您在建構函式中指定檔案名稱，該檔案會在物件建構時自動開啟。 或者，您可以在叫用預設建構函式之後使用 `open` 成員函式。

如同執行階段函式 `sprintf_s`，`ostringstream` 類別支援輸出至記憶體內字串。 若要使用 I/O 資料流格式在記憶體中建立字串，請建構類別 `ostringstream` 的物件。

## <a name="in-this-section"></a>本節內容

[建構輸出資料流物件](../standard-library/constructing-output-stream-objects.md)

[使用插入運算子和控制格式](../standard-library/using-insertion-operators-and-controlling-format.md)

[輸出檔資料流成員函式](../standard-library/output-file-stream-member-functions.md)

[緩衝的效果](../standard-library/effects-of-buffering.md)

[二進位輸出檔案](../standard-library/binary-output-files.md)

[為您的自訂類別多載 << 運算子](../standard-library/overloading-the-output-operator-for-your-own-classes.md)

[撰寫不含引數的操作工具](../standard-library/writing-your-own-manipulators-without-arguments.md)

## <a name="see-also"></a>另請參閱

[ofstream](../standard-library/basic-ofstream-class.md)\
[ostringstream](../standard-library/basic-ostringstream-class.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)
