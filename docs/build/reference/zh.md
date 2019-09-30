---
title: /ZH （在 [偵錯工具] 資訊中計算檔案總和檢查碼的雜湊演算法）
description: 使用/ZH 編譯器選項，在 debug 資訊中啟用 MD5、SHA-1 或 SHA-256 來源檔案總和檢查碼
ms.date: 09/16/2019
f1_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
helpviewer_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
- /ZH compiler option
- /ZH:MD5 compiler option
- /ZH:SHA1 compiler option
- /ZH:SHA_256 compiler option
- Hash algorithm for file checksum in debug info
ms.openlocfilehash: f05dc2bc3b8ce4502ff16a6e19fdbb10763b34ba
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686870"
---
# <a name="zh-hash-algorithm-for-calculation-of-file-checksum-in-debug-info"></a>/ZH （在 [偵錯工具] 資訊中計算檔案總和檢查碼的雜湊演算法）

指定要使用哪一種密碼編譯雜湊演算法來產生每個來源檔案的總和檢查碼。

## <a name="syntax"></a>語法

> **/ZH：** {**MD5**|**SHA1**|**SHA_256**}

## <a name="arguments"></a>引數

**/ZH： MD5**\
針對總和檢查碼使用 MD5 雜湊。 此選項是預設值。

**/ZH： SHA1**\
針對總和檢查碼使用 SHA-1 雜湊。

**/ZH： SHA_256**\
針對總和檢查碼使用 SHA-256 雜湊。

## <a name="remarks"></a>備註

PDB 檔案會針對編譯到相關聯可執行檔之物件程式碼中的每個來源檔案儲存總和檢查碼。 總和檢查碼可讓偵錯工具驗證所載入的原始程式碼是否符合可執行檔。 編譯器和偵錯工具支援 MD5、SHA-1 和 SHA-256 雜湊演算法。 根據預設，編譯器會使用 MD5 雜湊來產生總和檢查碼。 您可以使用 **/ZH： MD5**選項明確指定此選項。

由於 MD5 和 SHA-1 發生衝突的風險，Microsoft 建議您使用 **/ZH： SHA_256**選項。 在編譯時間中，SHA-256 雜湊可能會產生較小的增加。

當指定了一個以上的 **/ZH**選項時，就會使用最後一個選項。

從 Visual Studio 2019 16.4 版開始提供 **/ZH**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. **將 [設定**] 下拉式選為 [**所有**設定]。

1. 選取 [組態屬性] > [C/C++] > [命令列] 屬性頁。

1. 修改 [**其他選項**] 屬性以新增 **/ZH： MD5**、 **/ZH： SHA1**或 **/ZH： SHA_256**選項，然後選擇 **[確定]** 。

## <a name="see-also"></a>另請參閱

[編譯器選項](compiler-options.md)\
[來源伺服器](/windows/win32/debug/source-server-and-source-indexing)
