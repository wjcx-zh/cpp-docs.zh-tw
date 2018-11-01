---
title: 模組定義陳述式的規則
ms.date: 11/04/2016
f1_keywords:
- .def
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
ms.openlocfilehash: 6921043bd4618692be788ec5a61978f1178c64ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442766"
---
# <a name="rules-for-module-definition-statements"></a>模組定義陳述式的規則

下列語法規則套用至.def 檔案中的所有陳述式。 每個陳述式說明特定陳述式來套用其他規則。

- 陳述式、 屬性的關鍵字，以及使用者指定的識別碼會區分大小寫。

- 長時間的檔案名稱包含空格或分號 （;） 必須括在引號 （"）。

- 使用一或多個空格、 定位點或新行字元，將從其引數的陳述式關鍵字，以及不同彼此的陳述式。 冒號 （:） 或等號 （=），以指定引數必須括住的零或多個空格、 定位字元或新行字元。

- A**名稱**或是**程式庫**陳述式中，如果使用，必須在前面的所有其他陳述式。

- **各節**並**匯出**陳述式可以在.def 檔中出現一次以上。 每個陳述式可能需要多個規格，必須以一或多個空格、 定位點或新行字元分隔。 陳述式關鍵字必須出現一次之前的第一個規格，並且可以重複之前每個額外的規格。

- 許多陳述式都有一個相等的連結命令列選項。 請參閱對應的連結選項，如需詳細資訊的描述。

- .Def 檔案中的註解所指定的分號 （;） 的每個註解行開頭。 註解不能共用同一線路與陳述式，但它可以出現在多行陳述式中的規格之間。 (**各節**並**匯出**是多行陳述式。)

- 數值引數會指定基底 10 或十六進位。

- 如果字串引數符合[保留字](../../build/reference/reserved-words.md)，就必須括在雙引號 （"）。

## <a name="see-also"></a>另請參閱

[模組定義檔 (.Def)](../../build/reference/module-definition-dot-def-files.md)