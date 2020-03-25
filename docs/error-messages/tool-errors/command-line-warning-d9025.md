---
title: 命令列警告 D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: 4afd4d4dc07ffaae6038c025ee371278ebbebea6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196712"
---
# <a name="command-line-warning-d9025"></a>命令列警告 D9025

以 ' option2 ' 覆寫 ' option1 '

已指定*option1*選項，但之後已由*option2*覆寫。 已使用*option2*選項。

如果兩個選項指定了矛盾或不相容的指示詞，則會使用命令列上最右邊的選項中指定或隱含的指示詞。

如果您在從開發環境編譯時收到此警告，而且不確定衝突的選項來自何處，請考慮下列事項：

- 您可以在程式碼或專案的專案設定中指定選項。 如果您查看編譯器的[命令列屬性頁](../../build/reference/command-line-property-pages.md)，而且在 [**所有選項**] 欄位中看到衝突的選項，則會在專案的屬性頁中設定選項，否則會在原始程式碼中設定選項。

   如果是在專案的屬性頁中設定選項，請查看編譯器的 [預處理器] 屬性頁（已在方案總管中選取專案節點）。  如果您看不到 [設定] 選項，請檢查每個原始程式碼檔的 [預處理器] 屬性頁設定（方案總管），以確定它並未新增至該處。

   如果您在程式碼中設定選項，可以在程式碼或 windows 標頭中設定。  您可能會嘗試建立前置處理過的檔案（[/p](../../build/reference/p-preprocess-to-a-file.md)），然後搜尋該檔案中的符號。
