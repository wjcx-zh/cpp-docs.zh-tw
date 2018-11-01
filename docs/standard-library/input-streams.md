---
title: 輸入資料流
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
ms.openlocfilehash: 0f56f5ffc8e61c0881eddbbd65e1c431b9219674
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504763"
---
# <a name="input-streams"></a>輸入資料流

輸入資料流物件是位元組的來源。 三種最重要的輸入資料流類別為 [istream](../standard-library/basic-istream-class.md)、[ifstream](../standard-library/basic-ifstream-class.md) 及 [istringstream](../standard-library/basic-istringstream-class.md)。

`istream` 類別最適用於連續的文字模式輸入。 您可以設定 `istream` 類別的物件來進行經緩衝或未經緩衝的作業。 基底類別 `ios` 的所有功能都包含在 `istream` 中。 您極少會從 `istream` 類別建構物件。 您通常會改用預先定義的 `cin` 物件，而此物件實際上是 [ostream](../standard-library/basic-ostream-class.md) 類別的物件。 在某些情況下，您可以在程式啟動之後，將 `cin` 指派給其他資料流物件。

`ifstream` 類別支援磁碟檔案輸入。 如果您需要僅供輸入使用的磁碟檔案，請建構 `ifstream` 類別的物件。 您可以指定二進位或文字模式檔案。 如果您在建構函式中指定檔案名稱，則在建構完物件時會自動開啟該檔案。 否則，您可以在叫用預設建構函式之後，使用 `open` 函式。 許多格式設定選項和成員函式都適用於 `ifstream` 物件。 基底類別 `ios` 和 `istream` 的所有功能都包含在 `ifstream` 中。

與程式庫函式 `sscanf_s` 相同，`istringstream` 類別也支援從記憶體內的字串輸入。 若要從具有 Null 結束字元的字元陣列中擷取資料，請配置字串並將其初始化，然後建構 `istringstream` 類別的物件。

## <a name="in-this-section"></a>本節內容

[建構輸入資料流物件](../standard-library/constructing-input-stream-objects.md)

[使用擷取運算子](../standard-library/using-extraction-operators.md)

[測試是否有擷取錯誤](../standard-library/testing-for-extraction-errors.md)

[輸入資料流操作工具](../standard-library/input-stream-manipulators.md)

[輸入資料流成員函式](../standard-library/input-stream-member-functions.md)

[為您的自訂類別多載 >> 運算子](../standard-library/overloading-the-input-operator-for-your-own-classes.md)

## <a name="see-also"></a>另請參閱

[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
