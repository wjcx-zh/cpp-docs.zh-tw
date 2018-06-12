---
title: 移動定義位置 | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327836"
---
# <a name="move-definition-location"></a>移動定義位置
**功能：** 讓您立即將函式定義移至對應的標頭檔。

**時機：** 您有想要移動至標頭檔的函式。  

**原因：** 您可以手動移動函式，但這項功能會自動移動它，並建立必要的標頭檔。

**做法：**

1. 將文字或滑鼠游標置於您要移動的函式。

   ![醒目標示的程式碼](images/movedefinition_highlight.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從操作功能表選取 [移動定義位置]。
   * **滑鼠**
     * 以滑鼠右鍵按一下，選取 [快速動作與重構] 功能表，然後從操作功能表選取 [移動定義位置]。

1. 函式將會移至對應的標頭檔，您會在快顯預覽視窗中看到。  如果標頭檔不存在，它也會建立並放在專案中。

   ![建立宣告/定義結果](images/movedefinition_result.png)
