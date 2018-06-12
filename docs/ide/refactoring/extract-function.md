---
title: 擷取函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fc4d48c972bca9352f326085574e4cf4df83aea
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33333153"
---
# <a name="extract-function"></a>擷取函式
**功能：** 讓您將程式碼片段轉換成它自己的函式。

**時機：** 您在某個函式中有現有的程式碼片段，且必須從另一個函式呼叫。  

**原因：** 您可以複製/貼上該程式碼，但那樣會造成重複。  較的解決方案是將該片段重構成它自己的函式，以便由任何其他函式自由呼叫。

**做法：**

1. 醒目標示的擷取的程式碼：

   ![醒目標示的程式碼](images/extractfunction_highlight.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **CTRL+R**，再按 **CTRL+M**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從操作功能表選取 [擷取函式 (實驗)]。
   * **滑鼠**
     * 選取 [編輯] > [重構] > [擷取函式 (實驗)]。
     * 以滑鼠右鍵按一下程式碼，選取 [快速動作與重構] 功能表，然後從操作功能表選取 [擷取函式 (實驗)]。
     * 按一下出現在左邊界的![燈泡](images/bulb.png)圖示，然後從操作功能表選取 [擷取函式 (實驗)]。

1. 在 [擷取函式/方法 (實驗)] 視窗中，輸入新的函式名稱、選取您想執行程式碼的放置，並按一下 [確定] 按鈕。  

   ![擷取函式功能](images/extractfunction_dialog.png)

1. 將在您指定處建立新的函式，在對應的標頭檔中建立函式原型，並且會變更原始的程式碼以呼叫該函式。

   ![擷取函式結果](images/extractfunction_result.png)