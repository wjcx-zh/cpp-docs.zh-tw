---
title: 定義和慣例
ms.date: 11/04/2016
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
ms.openlocfilehash: 9da9a566ef0b8d34a1a3d64dd2b8ce659194e6ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226375"
---
# <a name="definitions-and-conventions"></a>定義和慣例

終端是語法定義的端點。 沒有其他解決方式。 終端包括一組保留字和使用者定義的識別項。

非終端是語法中的預留位置，會在此語法摘要中的其他地方定義。 定義可以是遞迴式。

選擇性元件是以下標<sub>opt</sub>表示。 例如

> **{** *expression*<sub>opt</sub> **}**

表示放在大括號中的選擇性運算式。

語法慣例會針對語法的不同元件使用不同的字型屬性。 符號和字型如下：

|屬性|說明|
|---------------|-----------------|
|*語法*|斜體類型表示非終端項。|
|**`const`**|粗體類型的終端項為必須依下述方式輸入的常值保留字和符號。 此內容中的字元一律區分大小寫。|
|<sub>opt</sub>|非終端項後面接著<sub>opt</sub>一律是選擇性的。|
|預設字樣|這個字樣中描述或列出的集合中的字元可用來作為 C 陳述式中的終端。|

接著非終端項的冒號 (**:**) 會引入其定義。 除非前面加上「one of」字樣，否則替代定義另列於其他行。

## <a name="see-also"></a>另請參閱

[C 語言語法摘要](../c-language/c-language-syntax-summary.md)
