---
title: HTML 的基本概念
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 63a866786abc3b1eaa87a06492b43b1c9e354882
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278381"
---
# <a name="html-basics"></a>HTML 的基本概念

大部分的瀏覽器有檢查您所瀏覽網頁的 HTML 原始檔的功能。 當您檢視原始碼時，您會看到一些 HTML (超文字標記語言) 標記，周圍以角括弧 (<>) 包圍，其中為文字。

下方的步驟使用 HTML 標記建立簡單的 Web 網頁。 在下列步驟中，您將在 [記事本] 本中輸入純文字到檔案中，進行一些變更，儲存檔案，並重新將網頁載入至瀏覽器中，以查看您的變更。

#### <a name="to-create-an-html-file"></a>若要建立的 HTML 檔案

1. 開啟 [記事本] 或任何純文字編輯器。

1. 從**檔案**功能表上，選擇**新增**。

1. 輸入下列各行：

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
</HTML>
```

1. 從**檔案**功能表上，選擇**儲存**，將檔案儲存另存為 c:\webpages\First.htm。 讓檔案在編輯器中保持開啟狀態。

1. 切換至您的瀏覽器，並從**檔案**功能表上，選擇**開放**，或型別*file://C:/webpages/first.htm*瀏覽器的 URL 編輯方塊中。 您應該會看到一個空白網頁，其視窗標題為 "Top HTML Tags"。

   請注意標記是成對的，而且會包含在角括弧中。 標記不區分大小寫，不過，大小寫通常用來讓標記引人注意。

   標記\<HTML > 啟動文件，與標記\</HTML > 結束它。 結束標記 (不一定需要) 與開始標記相似，不過，標記前方會有一個正斜線 (/)。 您不應該在角括弧 (<) 和標記之間保留空白。

1. 切換回 [記事本]，並在之後 \< /前端 > 行中，輸入：

```
<BODY>
    HTML is swell.
    Life is good.
</BODY>
```

1. 從**檔案**功能表上，選擇**儲存**。

1. 切換回您的瀏覽器並重新整理頁面。

   這些文字會出現在瀏覽器視窗的工作區中。 請注意，您的歸位字元會被忽略。 如果您想要分行，則必須在第一行的後方加上 `<BR>` 標記。

   所有步驟，請依照下列中，插入之間的任何位置的文字\<主體 > 和 \< /B > 新增至您的文件的本文。

9. 加入標題：

```
<H3>Here's the big picture</H3>
```

10. 使用儲存於和您的頁面相同目錄的 .gif 檔案來加入影像：

```
<IMG src="yourfile.gif">
```

11. 加入清單：

```
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
```

12. 清單進行編號，請使用配對\<OL > 並\</o l > 標記的位置\<u l > 和 \< /u l > 標記。

這可讓您開始使用。 如果您發現某個網頁的功能很不錯，可以藉由檢查 HTML 原始碼來了解其建立的方式。 HTML 編輯器 (如 Microsoft Front Page) 可用來建立簡單和進階的頁面。

以下是您建立的完整 HTML 原始檔：

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

如需標記的完整描述、屬性和副檔名，請參閱超文字標記語言 (HTML) 規格：

[最新發行的版本的 HTML](https://www.w3.org/TR/html/) W3C.org 在。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)
