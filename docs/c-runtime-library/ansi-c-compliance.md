---
title: ANSI C 合規性
description: 介紹 ANSI C 合規性的 Microsoft C 執行時間命名慣例。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Ansi
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
ms.openlocfilehash: 39a3f9299be7dbef4783faa8e6d08fe6ad8461f5
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590299"
---
# <a name="ansi-c-compliance"></a>ANSI C 合規性

執行階段系統中所有 Microsoft 特定識別碼 (例如函式、巨集、常數、變數與類型定義) 的命名慣例都符合 ANSI 標準。 在此文件中，依照 ANSI/ISO C 標準的所有執行階段函式都標示為與 ANSI 相容。 符合 ANSI 標準的應用程式應該只使用這些與 ANSI 相容的函式。

Microsoft 特定函式與全域變數的開頭都是一個底線字元。 這些名稱只能在程式碼的範圍內以區域方式覆寫。 例如，當您包含 Microsoft 執行階段標頭檔時，仍然能透過宣告相同名稱的區域變數，以區域方式覆寫名為 `_open` 的 Microsoft 特定函式。 然而，您無法為自己的全域函式或全域變數使用此名稱。

Microsoft 特定巨集與資訊清單常數名稱的開頭是兩個底線字元，或是一個前置底線字元加上一個大寫字母。 這些識別碼的範圍是絕對範圍。 例如，您無法針對此理由使用 Microsoft 特定識別碼 **_UPPER**。

## <a name="see-also"></a>另請參閱

[相容性](../c-runtime-library/compatibility.md)
