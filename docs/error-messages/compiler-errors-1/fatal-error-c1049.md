---
title: 嚴重錯誤 C1049
description: 描述編譯器嚴重錯誤 C1049、不正確數值引數，並說明如何解決此問題。
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: 9b3cbe5d081e32680e5408fc4a6ddcd932db77a2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503272"
---
# <a name="fatal-error-c1049"></a>嚴重錯誤 C1049

> 無效的數值引數*value*'

CL.EXE 命令列剖析器找到其預期數值引數的 *值* 。

當編譯器找不到其中一個編譯器選項的數值引數時，可能會發生 C1049 錯誤：

[/constexpr：深度](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr： backtrace](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr：步驟](../../build/reference/constexpr-control-constexpr-evaluation.md)

預期數值引數的命令列編譯器選項可能也會報告 `Command line error D8004` 、、、 `Command line error D8021` `Command line warning D9002` `Command line warning D9014` 或 `Command line warning D9024` 。

若要解決這個錯誤，請檢查命令列中是否有錯置或遺失的引數。 確認選項和引數之間沒有任何未預期的空格。 最後一個命令列可由宏、環境變數或其他組建系統作業產生。 這就是查看傳遞給編譯器的實際命令列很重要的原因。

- 在 [命令檔] 或 [makefile] 中，您可以使用 **echo** 命令來報告實際的命令列。

- 在 Visual Studio 中，開啟專案的 [ **屬性頁** ] 對話方塊。 在 [設定**屬性**  >  **C/c + +**  >  **一般**] 頁面上，將 [**隱藏啟動橫幅**] 屬性變更為 [**否**]。 選取 [確定]**** 儲存您的變更。 [ **輸出** ] 視窗現在會在您建立時，顯示在著作權線之後的命令列。

其他組建系統可能會有記錄檔或詳細資訊選項，以查看實際使用的命令。 如需詳細資訊，請參閱您的組建系統檔。
