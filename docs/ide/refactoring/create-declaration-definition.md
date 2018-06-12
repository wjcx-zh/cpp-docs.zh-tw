---
title: 建立宣告/定義 | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60d583ec47a3f9c5b61599a5945e3cfa0d375b1d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33331279"
---
# <a name="create-declaration--definition"></a>建立宣告/定義
**功能：** 可讓您立即產生函式的宣告或定義。

**時機：** 您有需要宣告的函式，反之亦然。  

**原因：** 您可以手動建立宣告/定義，但這會自動建立，並視需要建立標頭/程式碼檔案。

**做法：**

1. 將文字或滑鼠游標置於您要為其建立宣告或定義的函式。

   ![醒目標示的程式碼](images/createdefinition_highlight.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從操作功能表選取 [建立宣告/定義]。
   * **滑鼠**
     * 以滑鼠右鍵按一下，選取 [快速動作與重構] 功能表，然後從操作功能表選取 [建立宣告/定義]。

1. 函式的宣告/定義將會建立在來源或標頭檔中，您會在快顯預覽視窗中看到。  如果來源或標頭檔不存在，它也會建立並放在專案中。

   ![建立宣告/定義結果](images/createdefinition_result.png)
