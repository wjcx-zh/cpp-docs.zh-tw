---
title: 移動定義位置 |Microsoft 文件
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44211105429e33c136999a7877ac6ee42af29f17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="move-definition-location"></a>移動定義位置
**項目：**可讓您立即將函式定義移至對應的標頭檔。

**當：**具有您想要移動至標頭檔的函式。  

**原因：**您無法手動移動函式，但這項功能會移動它，自動建立必要的標頭檔。

**做法：**

1. 文字或滑鼠將游標置於您要移動的函數。

   ![醒目標示的程式碼](images/movedefinition_highlight.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 觸發程序**快速控制項目及重構**功能表，然後選取**移動定義位置**從內容功能表。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**移動定義位置**從內容功能表。

1. 此函式將會移至對應的標頭檔，您會看到快顯預覽視窗中。  如果標頭檔不存在，它也會是建立並放在專案中。

   ![建立宣告 / 定義產生](images/movedefinition_result.png)
