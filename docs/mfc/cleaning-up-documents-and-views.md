---
title: 清除文件和檢視
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 06ff60a2cf6245f64e80d899c13a8444558fcf0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374613"
---
# <a name="cleaning-up-documents-and-views"></a>清除文件和檢視

當文檔關閉時,框架首先調用其[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)成員函數。 如果您在文件的作業期間在堆積上配置任何記憶體，則 `DeleteContents` 是解除配置的最佳位置。

> [!NOTE]
> 您不應解除配置文件的解構函式中的文件資料。 在 SDI 應用程式案例中，可以重複使用文件物件。

您可以覆寫檢視的解構函式，以解除配置到堆積上的任何記憶體。

## <a name="see-also"></a>另請參閱

[初始化及清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)
