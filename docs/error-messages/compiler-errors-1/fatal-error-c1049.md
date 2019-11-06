---
title: 嚴重錯誤 C1049
description: 描述編譯器嚴重錯誤 C1049、不正確數值引數，並說明如何解決此問題。
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: f2669eec4bafb24f26c405d4fa74a96fe5337d13
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633193"
---
# <a name="fatal-error-c1049"></a>嚴重錯誤 C1049

> 無效的數值引數*value*'

CL。EXE 命令列剖析器找到需要數值引數的*值*。

當編譯器找不到下列其中一個編譯器選項的數值引數時，可能會發生 C1049 錯誤：

[/constexpr：深度](/cpp/build/reference/constexpr-control-constexpr-evaluation)\
[/constexpr： backtrace](/cpp/build/reference/constexpr-control-constexpr-evaluation)\
[/constexpr：步驟](/cpp/build/reference/constexpr-control-constexpr-evaluation)

預期數值引數的命令列編譯器選項可能也會報告 `Command line error D8004`、`Command line error D8021`、`Command line warning D9002`、`Command line warning D9014`或 `Command line warning D9024`。

若要解決這個錯誤，請檢查命令列中是否有錯置或遺漏引數。 確認選項和引數之間沒有非預期的空白。 最後的命令列可能是由宏、環境變數或其他組建系統作業所產生。 這就是為什麼要查看傳遞給編譯器的實際命令列是很重要的。

- 在命令檔或 makefile 中，您可以使用**echo**命令來報告實際的命令列。

- 在 Visual Studio 中，開啟專案的 [**屬性頁**] 對話方塊。 在 [**設定屬性** > **C/C++**  > **一般**] 頁面上，將 [**隱藏啟始**資訊] 內容變更為 [**否**]。 選取 [確定] 儲存您的變更。 當您建立時，[**輸出**] 視窗現在會顯示命令列，緊接在著作權線之後。

其他組建系統可能會有記錄檔或詳細資訊選項，以查看所使用的實際命令。 如需詳細資訊，請參閱您的組建系統檔。
