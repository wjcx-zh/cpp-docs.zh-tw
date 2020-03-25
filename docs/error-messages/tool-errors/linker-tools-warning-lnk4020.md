---
title: 連結器工具警告 LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: e818909cc0b590b0f7727846cfd7b469e8bc0e3f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194222"
---
# <a name="linker-tools-warning-lnk4020"></a>連結器工具警告 LNK4020

> '*filename*' 中的類型記錄已損毀;某些符號和類型可能無法從偵錯工具存取

PDB 檔案*檔案名*具有損毀的類型記錄。

此問題通常是其他組建問題的次要元件;除非這是第一個回報的組建問題，否則請先處理其他錯誤和警告。 如果這是第一個回報的問題，您可能需要清除組建目錄，並重建您的專案。 如果您使用平行組建進程，請參閱當您序列化組建時，錯誤是否持續發生。
