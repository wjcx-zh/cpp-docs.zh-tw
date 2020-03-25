---
title: 連結器工具警告 LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: fda1fdb03a7629894f846bb20ed84df519239327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183302"
---
# <a name="linker-tools-warning-lnk4102"></a>連結器工具警告 LNK4102

匯出刪除的析構函式 ' name ';映射可能無法正確執行

程式已嘗試匯出刪除的析構函式。 產生的刪除作業可能會跨 DLL 界限進行，讓進程可以釋放不屬於它的記憶體。 請確定指定的符號未列在 .def 檔中，而且該符號並未在連結器命令列中列為 **/IMPORT**或 **/export**選項的引數。

如果您要重建 C 執行時間程式庫，可以忽略此訊息。
