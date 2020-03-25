---
title: 連結器工具錯誤 LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: b18a93c7434ee3d66f42829f373bd916a65369bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195171"
---
# <a name="linker-tools-error-lnk1188"></a>連結器工具錯誤 LNK1188

BADFIXUPSECTION：：不正確修復目標 ' symbol ';可能的零長度區段

在 VxD 連結期間，重新配置的目標沒有區段。 使用 LINK386 （較舊版本）時，可能會使用 OMF 群組記錄（由 MASM GROUP 指示詞產生），將零長度區段與另一個非零長度區段結合。 COFF 格式不支援 GROUP 指示詞和零長度區段。 當連結自動將這種類型的 OMF 物件轉換成 COFF 時，可能會發生此錯誤。
