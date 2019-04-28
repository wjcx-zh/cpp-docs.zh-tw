---
title: 清除文件和檢視
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 940c768823d26950d9710fb1d1a52e6a1955fead
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327154"
---
# <a name="cleaning-up-documents-and-views"></a>清除文件和檢視

當文件正在關閉時，架構會先呼叫其[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)成員函式。 如果您在文件的作業期間在堆積上配置任何記憶體，則 `DeleteContents` 是解除配置的最佳位置。

> [!NOTE]
>  您不應解除配置文件的解構函式中的文件資料。 在 SDI 應用程式案例中，可以重複使用文件物件。

您可以覆寫檢視的解構函式，以解除配置到堆積上的任何記憶體。

## <a name="see-also"></a>另請參閱

[初始化及清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)
