---
title: 清除文件和檢視
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 1357a02379a848af23a6f78dee29e5b6adc1efcc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653891"
---
# <a name="cleaning-up-documents-and-views"></a>清除文件和檢視

當文件正在關閉時，架構會先呼叫其[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)成員函式。 如果您在文件的作業期間在堆積上配置任何記憶體，則 `DeleteContents` 是解除配置的最佳位置。

> [!NOTE]
>  您不應解除配置文件的解構函式中的文件資料。 在 SDI 應用程式案例中，可以重複使用文件物件。

您可以覆寫檢視的解構函式，以解除配置到堆積上的任何記憶體。

## <a name="see-also"></a>另請參閱

[初始化及清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)

