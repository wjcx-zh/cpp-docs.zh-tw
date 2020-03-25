---
title: 嚴重錯誤 C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: d094d0892d43a5f9894f03538f72e59b57bad6db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204460"
---
# <a name="fatal-error-c1054"></a>嚴重錯誤 C1054

編譯器限制：初始化運算式的嵌套太深

程式碼超過初始化運算式的嵌套限制（10-15 層級，視所要初始化的類型組合而定）。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 簡化要初始化的資料類型，以減少嵌套。

1. 在宣告之後的個別語句中初始化變數。
