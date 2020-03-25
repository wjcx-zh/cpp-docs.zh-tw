---
title: 嚴重錯誤 C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 76492be7abab6deb740f1670b85274b8c296c783
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203888"
---
# <a name="fatal-error-c1091"></a>嚴重錯誤 C1091

編譯器限制：字串長度超過 'length' 個位元組的上限

字串常數超過目前的字串長度限制。

您可能想要將靜態字串分割成兩個 (含) 以上的變數，並使用 [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 將結果聯結作為宣告的一部分或在執行階段時聯結。
