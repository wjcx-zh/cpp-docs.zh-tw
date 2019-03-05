---
title: 命令 ID
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: 76071105e72f1ca4a851b9cdb76d5f1a96f44edb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274568"
---
# <a name="command-ids"></a>命令 ID

命令的完整說明所單獨其命令識別碼 (編碼**WM_COMMAND**訊息)。 此識別碼被指派給產生命令的使用者介面物件。 一般而言，識別碼會命名為它們指派給使用者介面物件的功能。

比方說，在 編輯 功能表中的 全部清除項目可能會指派識別碼這類**ID_EDIT_CLEAR_ALL**。 類別庫預先定義的部分識別碼，特別是針對命令，架構會處理本身，例如**ID_EDIT_CLEAR_ALL**或是**ID_FILE_OPEN**。 您將會自行建立其他的命令 Id。

當您建立您自己的功能表中 Visual c + + 功能表編輯器時，它是個不錯的主意，請依照下列類別庫的命名慣例，如下圖所示**ID_FILE_OPEN**。 [標準命令](../mfc/standard-commands.md)說明標準類別程式庫所定義的命令。

## <a name="see-also"></a>另請參閱

[使用者介面物件和命令識別碼](../mfc/user-interface-objects-and-command-ids.md)
