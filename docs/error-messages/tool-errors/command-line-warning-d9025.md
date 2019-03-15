---
title: 命令列警告 D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: e7090dda72868ad7ee4d5f8e4f1ba6a0ad121c98
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822455"
---
# <a name="command-line-warning-d9025"></a>命令列警告 D9025

覆寫 '1' 與 'option2'

*Option1*選項已指定，但再覆寫*option2*。 *Option2*選項使用。

如果兩個選項指定了相衝突或不相容的指示詞，則會使用指定或隱含的最遠到右邊的選項，在命令列上的指示詞。

如果您從開發環境中，編譯時，收到這個警告，並不確定的選項衝突來自何處，請考慮下列各項：

- 在程式碼或專案的專案設定中，則可以指定選項。 如果您查看編譯器[命令列屬性頁](../../build/reference/command-line-property-pages.md)如果您看到中的選項衝突**所有選項**欄位則選項會設定在專案的屬性頁面中，否則選項在原始程式碼中設定。

   如果選項設定在專案屬性頁中，尋找編譯器前置處理器 屬性頁面上 （在 方案總管 中選取專案節點）。  如果您看不見的選項那里設定，請檢查並確定每個來源的程式碼檔案 （在 方案總管 中) 的前置處理器 屬性頁面設定它未在該處加入。

   如果在程式碼中設定的選項可以設定在程式碼或 windows 標頭。  您可能會嘗試建立前置處理過的檔案 ([/P](../../build/reference/p-preprocess-to-a-file.md))，並搜尋符號。