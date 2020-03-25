---
title: 轉換為原始字串常值
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: 5636e00bfe8655d84fb2e4b64e0391324ab35d7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171810"
---
# <a name="convert-to-raw-string-literal"></a>轉換為原始字串常值

**功能：** 可讓您將任何字串轉換成 C++ 原始字串常值。

**時機：** 您的字串裡有不應該處理為逸出字元的逸出字元。

**原因：** 您可以雙重逸出字元，但這通常會造成混淆且無法閱讀的字串。  使用原始字串常值，可讓字串更容易閱讀。

**方式：**

1. 將文字或滑鼠游標放在要轉換的逸出字串上。

   ![醒目標示的程式碼](images/stringliteral_highlight.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從操作功能表選取 [轉換為原始字串常值]。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼，選取 [快速動作與重構] 功能表，然後從操作功能表選取 [轉換為原始字串常值]。
     * 按一下出現在左邊界的![燈泡](images/bulb.png)圖示，然後從操作功能表選取 [轉換為原始字串常值]。

1. 字串將會立即轉換為原始字串常值。

   ![原始字串常值結果](images/stringliteral_result.png)
