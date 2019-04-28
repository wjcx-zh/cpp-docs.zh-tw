---
title: 專案建置警告 PRJ0042
ms.date: 08/27/2018
f1_keywords:
- PRJ0042
helpviewer_keywords:
- PRJ0042
ms.assetid: 682c9999-6f85-409f-b102-00c93243f74f
ms.openlocfilehash: c91e40b6ad56d6201fc7d0ba7c9fbf23e620e8b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297741"
---
# <a name="project-build-warning-prj0042"></a>專案建置警告 PRJ0042

> 檔案的自訂建置步驟的 '輸出屬性'*檔案*' 未設定。 將略過自訂建置步驟。

未執行自訂建置步驟，因為未指定輸出。

若要解決這個錯誤，請執行下列：

- 從組建中排除之自訂建置步驟。

- 加入輸出。

- 刪除自訂建置步驟之命令的內容。