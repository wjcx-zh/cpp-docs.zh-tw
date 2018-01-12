---
title: "原始字串常值轉換成 |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12aa512270ecce4564561634f99be9cbf155448a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="convert-to-raw-string-literal"></a>轉換為原始字串常值
**項目：**可讓您將任何字串轉換成 c + + 原始字串常值。

**當：**有不應該處理為逸出字元逸出字元的字串。

**原因：**無法雙逸出字元，但這通常會造成混淆且無法讀取的字串將導致。  使用原始字串常值，可讓字串更容易讀取。

**如何：**

1. 您可以將文字或滑鼠游標放要轉換的逸出字串。

   ![反白顯示的程式碼](images/stringliteral_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**原始字串常值轉換成**從內容功能表。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**原始字串常值轉換成**從內容功能表。
     * 按一下![Lightbulb](images/bulb.png)圖示出現在左邊的界，然後選取**原始字串常值轉換成**從內容功能表。

1. 字串將會立即轉換為原始字串常值。  

   ![原始字串常值的結果](images/stringliteral_result.png)