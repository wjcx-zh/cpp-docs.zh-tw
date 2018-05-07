---
title: 原始字串常值轉換成 |Microsoft 文件
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b98825719e7b3c0d8eb760a2ec50644b5eddd54e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="convert-to-raw-string-literal"></a>轉換為原始字串常值
**項目：**可讓您將任何字串轉換成 c + + 原始字串常值。

**當：**有不應該處理為逸出字元逸出字元的字串。

**原因：**無法雙逸出字元，但這通常會造成混淆且無法讀取的字串將導致。  使用原始字串常值，可讓字串更容易讀取。

**做法：**

1. 您可以將文字或滑鼠游標放要轉換的逸出字串。

   ![醒目標示的程式碼](images/stringliteral_highlight.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 觸發程序**快速控制項目及重構**功能表，然後選取**原始字串常值轉換成**從內容功能表。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**原始字串常值轉換成**從內容功能表。
     * 按一下![Lightbulb](images/bulb.png)圖示出現在左邊的界，然後選取**原始字串常值轉換成**從內容功能表。

1. 字串將會立即轉換為原始字串常值。  

   ![原始字串常值的結果](images/stringliteral_result.png)