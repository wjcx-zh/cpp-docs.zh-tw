---
title: 專案建置錯誤 PRJ0002 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0002
dev_langs:
- C++
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc0e48130c17e04c2671395161452c9e66000047
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195711"
---
# <a name="project-build-error-prj0002"></a>專案建置錯誤 PRJ0002

> 從傳回的錯誤結果 '*命令列*'。

命令，*命令列*，其中的格式，從使用者輸入中**屬性頁**對話方塊中，傳回錯誤碼，但沒有資訊會出現在**輸出**視窗.

此錯誤的解決方法取決於哪一項工具會產生錯誤。 MIDL，您會了解可能的問題出在哪裡，如果 /o （重新導向的輸出） 定義。

批次檔，例如自訂建置步驟或建置事件，不是失敗狀況的相關資訊也可能造成此錯誤的原因。