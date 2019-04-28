---
title: 連結器工具錯誤 LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: 69ac20522aebb7391319c0de210e06b305f3fd0d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226474"
---
# <a name="linker-tools-error-lnk1188"></a>連結器工具錯誤 LNK1188

BADFIXUPSECTION:: 無效的修復目標 'symbol';可能為零長度區段

VxD 連結期間的重新放置目標沒有一節。 使用 LINK386 （較舊版本），（MASM 群組指示詞所產生） 的 OMF 群組記錄可能已用來結合區段的另一個非零長度的零長度區段。 COFF 格式不支援在 GROUP 指示詞和長度為零的區段。 當連結會自動將此類型的 OMF 物件轉換成 COFF 時，可能會發生此錯誤。