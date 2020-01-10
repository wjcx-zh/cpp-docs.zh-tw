---
title: 標記和字元集
ms.date: 12/10/2019
helpviewer_keywords:
- Tokens (C++)
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 1f6dbe2faa6348d61ec00b411cc35e8ef5ceb57a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301609"
---
# <a name="tokens-and-character-sets"></a>標記和字元集

C++程式的文字包含標記和*空白字元*。 語彙基元是 C++ 程式中對編譯器有意義的最小項目。 C++剖析器會辨識這類權杖：

- [關鍵字](../cpp/keywords-cpp.md)
- [識別項](../cpp/identifiers-cpp.md)
- [數值、布林值和指標常值](../cpp/numeric-boolean-and-pointer-literals-cpp.md)
- [字串和字元常值](../cpp/string-and-character-literals-cpp.md)
- [使用者定義常值](../cpp/user-defined-literals-cpp.md)
- [運算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
- [標點符號](../cpp/punctuators-cpp.md)

標記通常會以*空白字元*分隔，這可以是一或多個：

- 空白
- 水平或垂直定位字元
- 新行
- 表單摘要
- 註解

## <a name="basic-source-character-set"></a>基本來源字元集

C++標準指定可用於原始程式檔的*基本來源字元集*。 為了表示不在這個集合中的字元，還可使用 *「通用字元名稱」* (Universal Character Name) 來指定額外的字元。 MSVC 執行允許額外的字元。 *基本來源字元集*是由可用於原始程式檔中的96個字元所組成。 這個集合包含空白字元、水平定位字元、垂直定位字元、換頁字元和換行控制字元，以及下列一組圖形字元：

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Microsoft 專屬**

MSVC 會將 `$` 字元包含為基本來源字元集的成員。 MSVC 也允許根據檔案編碼，在原始程式檔中使用一組額外的字元。 根據預設，Visual Studio 會使用預設字碼頁來儲存原始程式檔。 當使用地區設定特定字碼頁或 Unicode 字碼頁來儲存原始程式檔時，MSVC 可讓您在原始程式碼中使用該字碼頁的任何字元，但基本來源字元集中未明確允許的控制碼除外。 例如，如果您使用日文字碼頁來儲存檔案，則可以將日文字元放在註解、識別項或字串常值中。 MSVC 不允許無法轉譯成有效多位元組字元或 Unicode 程式碼點的字元序列。 根據編譯器選項，並非所有允許的字元都可出現在識別項中。 如需詳細資訊，請參閱 [Identifiers](../cpp/identifiers-cpp.md)。

**結束 Microsoft 專屬**

### <a name="universal-character-names"></a>通用字元名稱

由於 C++ 程式可以使用比基本來源字元集所指定的字元還要多的字元，因此您可以使用 *「通用字元名稱」* (Universal Character Name)，透過移植的方式來指定這些字元。 通用字元名稱是由代表 Unicode 字碼指標的字元序列所組成。  這些字元採用兩種格式。 使用 `\UNNNNNNNN` 來表示 U+NNNNNNNN 格式的 Unicode 字碼指標，其中 NNNNNNNN 是八位數的十六進位字碼指標數字。 使用四位數的 `\uNNNN` 來表示 U+0000NNNN 格式的 Unicode 字碼指標。

通用字元名稱可用於識別項、字串和字元常值中。 通用字元名稱不可用來代表範圍 0xD800-0xDFFF 中的 Surrogate 字碼指標。 請改用想要的字碼指標；編譯器會自動產生任何必要的 Surrogate。 可用於識別項的通用字元名稱還有其他限制。 如需詳細資訊，請參閱 [Identifiers](../cpp/identifiers-cpp.md) 和 [String and Character Literals](../cpp/string-and-character-literals-cpp.md)。

**Microsoft 專屬**

Microsoft C++編譯器會將通用字元名稱格式的字元與常值形式交換。 例如，您可以使用通用字元名稱格式宣告一個識別項，然後以常值格式來使用該識別項：

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Windows [剪貼簿] 上的擴充字元格式會因應用程式地區設定而有所不同。 將這些字元從另一個應用程式剪下並貼到您的程式碼可能會採用未預期的字元編碼方式。 這會導致程式碼中出現沒有明顯原因的剖析錯誤。 建議您先將原始程式檔編碼方式設定為 Unicode 字碼頁，再剖析擴充字元。 此外，也建議您使用 IME 或字元對應表應用程式來產生擴充字元。

**結束 Microsoft 專屬**

### <a name="execution-character-sets"></a>執行字元集

*執行字元集*代表可以在已編譯器中出現的字元和字串。 這些字元集是由原始程式檔中允許的所有字元所組成，以及代表警示、倒退鍵、回車和 null 字元的控制字元。 執行字元集具有地區設定特定表示法。
