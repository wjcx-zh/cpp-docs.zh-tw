---
title: 使用者帳戶控制 (UAC) 如何影響應用程式
ms.date: 11/19/2018
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
ms.openlocfilehash: 3702462ec892025cfb4f24d9c91e6db705b1b9a5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751398"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>使用者帳戶控制 (UAC) 如何影響應用程式

使用者帳戶控制 (UAC) 是 Windows Vista 的功能，可以讓使用者帳戶擁有有限的權限。 您可以在以下網站找到有關 UAC 的詳細資訊：

- [開發人員最佳實務和最小權限的環境中的應用程式的指導方針](/windows/desktop/uxguide/winenv-uac)

## <a name="building-projects-after-enabling-uac"></a>在啟用 UAC 後建置專案

如果您在停用 UAC 的情況下，在 Windows Vista 上建置 Visual C++ 專案，而且在稍後啟用了 UAC，就必須清除及重新建置專案，才能夠使其正確運作。

## <a name="applications-that-require-administrative-privileges"></a>需要系統管理員權限的應用程式

根據預設，Visual c + + 連結器將 UAC 片段內嵌到應用程式的執行層級的資訊清單`asInvoker`。 如果您的應用程式需要系統管理員權限才能正確執行 (例如，如果會修改登錄的 HKLM 節點，或是會寫入到磁碟上受保護的區域，如 Windows 目錄)，您就必須修改應用程式。

第一個選項是修改要變更的執行層級的資訊清單的 UAC 片段*requireAdministrator*。 然後，應用程式便會提示使用者，必須在執行前提供管理認證。 如需如何執行這項操作的資訊，請參閱[/MANIFESTUAC （將 UAC 資訊內嵌在資訊清單中）](../build/reference/manifestuac-embeds-uac-information-in-manifest.md)。

第二個選項則是指定 `/MANIFESTUAC:NO` 連結器選項，讓 UAC 片段不要內嵌到資訊清單中。 在此情況下，您的應用程式便會以虛擬化的方式執行。 您對登錄或檔案系統所做的任何變更，都不會在應用程式結束後持續。

下列流程圖描述應用程式將會如何根據是否有啟用 UAC，以及應用程式是否有 UAC 資訊清單來執行。

![Windows 載入器行為](media/uacflowchart.png "Windows 載入器行為")

## <a name="see-also"></a>另請參閱

[安全性最佳做法](security-best-practices-for-cpp.md)
