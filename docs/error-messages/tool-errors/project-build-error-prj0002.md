---
title: 專案建置錯誤 PRJ0002
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: d8e13bcc03a02fd9dbc739566a92025a7b97d598
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516268"
---
# <a name="project-build-error-prj0002"></a>專案建置錯誤 PRJ0002

> 從傳回的錯誤結果 '*命令列*'。

命令，*命令列*，其中的格式，從使用者輸入中**屬性頁**對話方塊中，傳回錯誤碼，但沒有資訊會出現在**輸出**視窗.

此錯誤的解決方法取決於哪一項工具會產生錯誤。 MIDL，您會了解可能的問題出在哪裡，如果 /o （重新導向的輸出） 定義。

批次檔，例如自訂建置步驟或建置事件，不是失敗狀況的相關資訊也可能造成此錯誤的原因。