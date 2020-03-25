---
title: 在 Visual Studio 中使用 Live Share for C++ 進行共同作業
description: 在 Visual Studio 中使用 Live Share for C++ 可即時對程式碼進行共同作業並予以共用。
ms.date: 05/24/2019
ms.openlocfilehash: e8202cefb7f7d762e2736edcd5fa3c6127b4affa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171914"
---
# <a name="collaborate-using-live-share-for-c"></a>使用適用於 C++ 的 Live Share 共同作業

在 Visual Studio 2019 和 Visual Studio Code 中，您可以使用 **Live Share** 對 C++ 專案進行即時共同作業。 有了 **Live Share**，其他人可以編輯程式碼並對其進行偵錯，而不需要安裝您的專案或其任何相依性。 您會看到彼此的編輯內容，且每項編輯內容都會以進行編輯的人員名稱加以標記。

![C&#43; &#43; Live Share 編輯](../ide/media/live-share-edit-cpp.png "Live Share 在中編輯C++")

## <a name="live-share-host-and-guests"></a>Live Share 主持人和來賓

在 Live Share 工作階段中，有一位主持人和一或多位來賓。 主持人和來賓都可以使用 Visual Studio 或 Visual Studio Code。 Windows 上的 Visual Studio 2019 主持人可以與 Linux 上的 Visual Studio Code 來賓分享。

主持人會為來賓提供他們提高生產力所需的一切項目。 來賓不需要具備原始程式碼、編譯器、外部相依性，甚至是相同的安裝元件。

主持人和來賓可以使用以下 IntelliSense 功能：

- 成員清單
- 參數說明
- 快速諮詢
- 偵錯/中斷點
- 尋找所有參考
- 移至定義
- 符號搜尋 (Ctrl+T)
- 反白顯示參考
- 診斷/錯誤/波浪線

![C&#43; &#43; Live Share 的調試](../ide/media/live-share-debug-cpp.png "Live Share 在中的調試C++")

## <a name="start-and-end-a-live-share-session"></a>開始及結束 Live Share 工作階段

若要在 Visual Studio 中啟動 Live Share 工作階段，請按一下右上方的 [共用] 按鈕，或移至 [檔案] > [開始共同作業工作階段]。 這會產生一個您可以與共同作業者共用的連結。

![C&#43; &#43; Live Share 按鈕](../ide/media/live-share-button-cpp.png "Live Share 按鈕")

若要結束工作階段，請從 [共用] 下拉式清單中選取 [結束共同作業工作階段]。

![C&#43; &#43; Live Share 按鈕](../ide/media/live-share-end-session-cpp.png "Live Share 按鈕")

## <a name="for-more-information"></a>取得詳細資訊

如需 Visual Studio 中 **Live Share** 的詳細資訊，請參閱[＜什麼是 Visual Studio Live Share？＞](/visualstudio/liveshare/)。 如需 Visual Studio Code 中 Live Share 的詳細資訊，請參閱 [Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare)。

## <a name="see-also"></a>另請參閱

[編輯及重構程式碼 (C++)](writing-and-refactoring-code-cpp.md)</br>
[在 Visual Studio 中巡覽 C++ 程式碼基底](navigate-code-cpp.md)</br>
[閱讀並了解 C++ 程式碼](read-and-understand-code-cpp.md)</br>
