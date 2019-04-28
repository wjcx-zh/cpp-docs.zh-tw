---
title: 連結器工具警告 LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: 0f9c8649988dd3056e98730ac4b02022a8c9dd51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327258"
---
# <a name="linker-tools-warning-lnk4102"></a>連結器工具警告 LNK4102

刪除解構函式 'name;' 的匯出映像可能無法正確執行

程式已嘗試匯出刪除解構函式。 產生的刪除可能會發生跨 DLL 界限，使得處理程序可以釋放它沒有自己的記憶體。 確定指定的符號不在.def 檔案中，所列，而且符號未列為的引數 **/ 匯入**或是 **/匯出**連結器命令列中的選項。

如果您重建 C 執行階段程式庫，您可以忽略此訊息。