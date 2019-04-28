---
title: 專案建置警告 PRJ0029
ms.date: 11/04/2016
f1_keywords:
- PRJ0029
helpviewer_keywords:
- PRJ0029
ms.assetid: f02c09c6-09f3-4d44-8cd4-9a25336be1ea
ms.openlocfilehash: 1daac3435bc8f1b4bd4ed8462caf3b8eaa397e22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298031"
---
# <a name="project-build-warning-prj0029"></a>專案建置警告 PRJ0029

專案層級自訂建置步驟的 'Outputs' 屬性未設定。 將略過自訂建置步驟。

未執行自訂建置步驟，因為未指定輸出。

若要解決這個錯誤，請執行下列：

- 從組建中排除之自訂建置步驟。

- 加入輸出。

- 刪除自訂建置步驟之命令的內容。