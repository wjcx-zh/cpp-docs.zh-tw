---
title: 嚴重錯誤 C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: 0bfd0c03378b1a9c616a014ac96153b3ab04af9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569193"
---
# <a name="fatal-error-c1054"></a>嚴重錯誤 C1054

編譯器限制： 初始設定式巢狀太深

程式碼超過初始設定式 （10 至 15 層級，根據正在初始化的類型的組合） 的巢狀限制。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 簡化的資料類型，以減少巢狀結構正在初始化。

1. 初始化個別的陳述式中的變數宣告之後。