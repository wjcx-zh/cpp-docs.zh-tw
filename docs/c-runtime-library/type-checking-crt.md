---
title: 類型檢查 (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.types
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
ms.openlocfilehash: bb5aecc2b47aa8e88666f42d8022395bf99fd85e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747679"
---
# <a name="type-checking-crt"></a>類型檢查 (CRT)

編譯器會在可接受不定數目引數的函式上執行有限的類型檢查，如下所示：

|函式呼叫 |經類型檢查的引數|
|-------------------|-----------------------------|
|`_cprintf_s`、`_cscanf_s`、`printf_s``scanf_s`|第一個引數 (格式字串)|
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|前兩個引數 (檔案或緩衝區與格式字串)|
|`_snprintf_s`|前三個引數 (檔案或緩衝區、計數，以及格式字串)|
|`_open`|前兩個引數 (路徑與 `_open` 旗標)|
|`_sopen_s`|前三個引數 (路徑、`_open` 旗標與共用模式)|
|`_execl`、`_execle`、`_execlp`、`_execlpe`|前兩個引數 (路徑與第一個引數指標)|
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|前三個引數 (模式旗標、路徑與第一個引數指標)|

編譯器會在這些函式的寬字元對等項目上執行相同的有限類型檢查。

## <a name="see-also"></a>另請參閱

[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
