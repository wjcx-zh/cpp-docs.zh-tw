---
title: 專案建置錯誤 PRJ0019
ms.date: 11/04/2016
f1_keywords:
- PRJ0019
helpviewer_keywords:
- PRJ0019
ms.assetid: 5390a62b-aacf-4bc8-b9d7-08f1e0233423
ms.openlocfilehash: 3aed7ca5dcf5803305d8765f50430520a5b73d2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192532"
---
# <a name="project-build-error-prj0019"></a>專案建置錯誤 PRJ0019

工具從傳回錯誤碼

自訂群組建步驟或組建事件的錯誤層級不是零。

當工具傳回錯誤碼但沒有錯誤訊息時，您也會看到 PRJ0019。 例如，如果您將 MIDL 的輸出重新導向至 NUL，就會發生這種情況。

如需詳細資訊，請參閱針對[自訂群組建步驟和組建事件進行疑難排解](../../build/troubleshooting-build-customizations.md)。

當您以 Users 群組的成員身分執行，而且需要系統管理存取權時，也可能會發生此錯誤。 如需詳細資訊，請參閱[以使用者群組的成員](../../security/running-as-a-member-of-the-users-group.md)身分執行。
