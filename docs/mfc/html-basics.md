---
title: HTML 的基本概念
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 29ca2e3df4981db22a10281ba2a2938fc91d5b46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620007"
---
# <a name="html-basics"></a>HTML 的基本概念

大部分的瀏覽器有檢查您所瀏覽網頁的 HTML 原始檔的功能。 當您查看來源時，您會看到一些 HTML （超文字標記語言）標記，並以角括弧（<>）括住，並與文字交錯。

下方的步驟使用 HTML 標記建立簡單的 Web 網頁。 在下列步驟中，您將在 [記事本] 本中輸入純文字到檔案中，進行一些變更，儲存檔案，並重新將網頁載入至瀏覽器中，以查看您的變更。

#### <a name="to-create-an-html-file"></a>若要建立 HTML 檔案

1. 開啟 [記事本] 或任何純文字編輯器。

1. 從 [檔案 **] 功能表選擇 [** **新增**]。

1. 輸入下列各行：

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. 從 [檔案 **] 功能表中，選擇 [** **儲存**]，然後將檔案儲存為 c： \ 網頁 \ First .htm。 讓檔案在編輯器中保持開啟狀態。

1. 切換至您的瀏覽器，然後從 [檔案 **] 功能表中選擇 [** **開啟**]，或在瀏覽器的 URL 編輯方塊中輸入*file://C:/webpages/first.htm* 。 您應該會看到一個空白網頁，其視窗標題為 "Top HTML Tags"。

   請注意標記是成對的，而且會包含在角括弧中。 標記不區分大小寫，不過，大小寫通常用來讓標記引人注意。

   標記 \<HTML> 會開機檔案，而標記 \</HTML> 會結束。 結束標記 (不一定需要) 與開始標記相似，不過，標記前方會有一個正斜線 (/)。 角括弧（<）與標記開頭之間不應該有空格。

1. 切換回 [記事本]，然後在 \</HEAD> 行之後輸入：

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. 從 [檔案 **] 功能表中，選擇 [** **儲存**]。

1. 切換回您的瀏覽器並重新整理頁面。

   這些文字會出現在瀏覽器視窗的工作區中。 請注意，您的歸位字元會被忽略。 如果您想要分行，則必須在第一行的後方加上 `<BR>` 標記。

   針對後面的所有步驟，在和之間插入文字， \<BODY> \</BODY> 以加入至您的檔主體。

1. 加入標題：

    ```html
    <H3>Here's the big picture</H3>
    ```

1. 使用儲存於和您的頁面相同目錄的 .gif 檔案來加入影像：

    ```html
    <IMG src="yourfile.gif">
    ```

1. 加入清單：

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. 若要改為將清單編號，請使用配對的 \<OL> 和 \</OL> 標記來取代 \<UL> 和 \</UL> 標記。

這可讓您開始使用。 如果您發現某個網頁的功能很不錯，可以藉由檢查 HTML 原始碼來了解其建立的方式。 HTML 編輯器 (如 Microsoft Front Page) 可用來建立簡單和進階的頁面。

以下是您建立的完整 HTML 原始檔：

```html
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

W3C.org[最新發行的 HTML 版本](https://www.w3.org/TR/html/)。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計基本概念](mfc-internet-programming-basics.md)
