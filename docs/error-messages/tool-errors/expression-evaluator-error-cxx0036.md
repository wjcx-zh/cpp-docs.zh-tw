---
title: 運算式評估工具錯誤 CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: 164fd9ee00071e218e5bb4f3ab00febc618725a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195496"
---
# <a name="expression-evaluator-error-cxx0036"></a>運算式評估工具錯誤 CXX0036

錯誤的內容 {...} 規格

此訊息可以由內容運算子（ **{}** ）中的任何一個錯誤所產生。

- 未正確指定內容運算子（ **{}** ）的語法。

   內容運算子的語法為：

     {*function*，*module*，*dll*}*運算式*

   這會指定*運算式*的內容。 內容運算子與類型轉換具有相同的優先順序和使用方式。

   可以省略尾端逗號。 如果任何函式、*模組*或*dll*包含常值*逗號，您*必須將整個名稱括在括弧中。

- 函式名稱拼寫錯誤，或不存在於指定的模組或動態連結程式庫中。

   因為 C 是區分大小寫的*語言，所以*必須以在來源中定義的確切大小寫方式來提供函式。

- 找不到模組或 DLL。

   檢查指定之模組或 DLL 的完整路徑名稱。

此錯誤與 CAN0036 相同。
