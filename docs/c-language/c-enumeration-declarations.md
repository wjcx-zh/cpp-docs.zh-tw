---
title: C 列舉宣告 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 858f7bf440b0a53a7e9ed5bb666029b7d1135f81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091890"
---
# <a name="c-enumeration-declarations"></a>C 列舉宣告

列舉是由一組具名整數常數所組成。 列舉類型宣告會提供 (選擇性) 列舉標記的名稱，以及定義具名整數識別項集合 (稱為「列舉集合」、「列舉程式常數」、「列舉程式」或「成員」)。 具有列舉類型的變數會儲存該類型所定義列舉集合的其中一個值。

`enum` 類型的變數可以在索引運算式中使用，以及做為所有算術和關係運算子的運算元使用。 列舉提供了 `#define` 前置處理器指示詞的替代方式，具有自動產生值並遵循一般範圍規則的優點。

在 ANSI C 中，定義列舉程式常數值的運算式一律具有 `int` 類型，因此，與列舉變數相關聯的儲存區會是單一 `int` 值所需的儲存區。 列舉常數或列舉類型的值可以在 C 語言允許使用整數運算式的任何位置使用。

## <a name="syntax"></a>語法

*enum-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *識別碼*<sub>opt</sub> **{** *enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *識別碼*

選擇性的 *identifier* 會為 *enumerator-list* 所定義的列舉類型命名。 這個識別項通常稱為清單所指定列舉的「標記」。 下列這種形式的類型規範

```
enum identifier
{
    enumerator-list
}
```

會將 *identifier* 宣告為 *enumerator-list* 非終端項所指定的列舉標記。 *enumerator-list* 會定義「列舉程式內容」。 *enumerator-list* 的詳細說明如下。

如果標記的宣告可見，則使用該標記但省略 *enumerator-list* 的後續宣告會指定先前宣告的列舉類型。 標記必須參考已定義的列舉類型，而且該列舉類型必須在目前範圍內。 由於列舉類型是在他處所定義，因此 *enumerator-list* 不會出現在這個宣告中。 衍生自列舉的類型宣告和列舉類型的 `typedef` 宣告，可以在列舉類型定義之前使用列舉標記。

## <a name="syntax"></a>語法

*enumerator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉程式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator-list* **,** *列舉程式*

*列舉程式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant* **=** *constant-expression*

*enumeration-constant*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*enumeration-list* 中的每個 *enumeration-constant*都會為列舉集合命名。 根據預設，第一個 *enumeration-constant* 會與值 0 相關聯。 清單中的下一個 *enumeration-constant* 會與 ( *constant-expression* + 1 ) 的值相關聯，除非您明確將它與另一個值產生關聯。 *enumeration-constant* 的名稱相當於其值。

您可以使用 *enumeration-constant = constant-expression* 覆寫值的預設順序。 因此，如果 *enumeration-constant = constant-expression* 出現在 *enumerator-list* 中，*enumeration-constant* 就會與 *constant-expression* 所產生的值相關聯。 *constant-expression* 必須具有 `int` 類型，而且可以是負數。

下列規則適用於列舉集合的成員：

- 列舉集合可以包含重複的常數值。 例如，您可以將值 0 與相同集合中兩個可能名為 `null` 和 `zero` 的不同識別項產生關聯。

- 列舉清單中的識別項必須與相同範圍中具有相同可視性的其他識別項有所區別，包括其他列舉清單中的一般變數名稱和識別項。

- 列舉標記會遵循一般範圍規則。 它們必須與具有相同可視性的其他列舉、結構和等位標記有所區別。

## <a name="examples"></a>範例

下面這些範例將說明列舉宣告：

```
enum DAY            /* Defines an enumeration type    */
{
    saturday,       /* Names day and declares a       */
    sunday = 0,     /* variable named workday with    */
    monday,         /* that type                      */
    tuesday,
    wednesday,      /* wednesday is associated with 3 */
    thursday,
    friday
} workday;
```

根據預設，值 0 會與 `saturday` 相關聯。 識別項 `sunday` 明確設定為 0。 其餘識別項的預設值為 1 至 5。

在這個範例中，`DAY` 集合中的值會指派給 `today` 變數。

```
enum DAY today = wednesday;
```

請注意，列舉常數的名稱會用來指派值。 由於先前已宣告 `DAY` 列舉類型，因此只有列舉標記 `DAY` 是必要的。

若要將整數值明確指派給列舉資料類型的變數，請使用類型轉換：

```
workday = ( enum DAY ) ( day_value - 1 );
```

建議您在 C 中使用這項轉型，但並非必要。

```
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

這個宣告也可以指定為

```
enum BOOLEAN { false, true } end_flag, match_flag;\
```

或為

```
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

使用這些變數的範例如下所示：

```
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

您也可以宣告未命名的列舉資料類型。 資料類型的名稱會加以省略，但是可以宣告變數。 變數 `response` 是所定義類型的變數：

```
enum { yes, no } response;
```

## <a name="see-also"></a>請參閱

[列舉](../cpp/enumerations-cpp.md)