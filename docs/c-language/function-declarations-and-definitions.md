---
title: 函式宣告和定義 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- local declarations
- function definitions, function declarations
- declaring functions, function definitions
- internal declarations
- external declarations
- function prototypes, basics
- external linkage, function declarations
- declaring functions
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2bb5a6b1f184775b3e67a03b9544e609b33673ba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106118"
---
# <a name="function-declarations-and-definitions"></a>函式宣告和定義

函式原型會建立函式的名稱、其傳回型別，以及其正式參數的類型和數目。 函式定義包括函式主體。

## <a name="remarks"></a>備註

函式和變數宣告都可以出現在函式定義的內部或外部。 函式定義內的任何宣告一般會稱為出現在「內部」或「區域」層級。 在所有函式定義外部的宣告則稱為出現在「外部」、「全域」或「檔案範圍」層級。 變數定義 (像是宣告) 可能會出現在內部層級 (在函式定義內) 或外部層級 (在所有函式定義外)。 函式定義一律在外部層級發生。 函式定義將在[函式定義](../c-language/c-function-definitions.md)中進一步討論。 函式原型將涵蓋在[函式原型](../c-language/function-prototypes.md)中。

## <a name="see-also"></a>請參閱

[原始程式檔和來源程式](../c-language/source-files-and-source-programs.md)