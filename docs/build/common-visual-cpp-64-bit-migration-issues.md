---
title: Visual C++ 64 位元移轉時常見的問題
ms.date: 05/06/2019
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: 68f4dc4276c5cbce687477ca25ec69f0cb544acb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229853"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Visual C++ 64 位元移轉時常見的問題

當您使用 Microsoft c + + 編譯器（MSVC）來建立要在64位 Windows 作業系統上執行的應用程式時，您應該注意下列問題：

- **`int`** 和是 **`long`** 64 位 Windows 作業系統上的32位值。 對於您要為 64 位元平台進行編譯的程式，您應小心不要將指標指派給 32 位元變數。 指標在 64 位元平台上是 64 位元的，如果您將指標指派給 32 位元變數，將會截斷指標值。

- `size_t`、 `time_t` 和 `ptrdiff_t` 是64位 Windows 作業系統上的64位值。

- `time_t`在 Visual Studio 2005 和更早版本中，在32位 Windows 作業系統上是32位的值。 `time_t` 現在預設為 64 位元整數。 如需詳細資訊，請參閱[時間管理](../c-runtime-library/time-management.md)。

   您應該知道您的程式碼接受值的位置 **`int`** ，並將其處理為 `size_t` 或 `time_t` 值。 數位可能會成長到大於32位的數位，且資料會在傳回儲存體時被截斷 **`int`** 。

% X （十六進位 **`int`** 格式） `printf` 修飾詞在64位 Windows 作業系統上將無法如預期般運作。 它只會處理傳遞給它之值的前 32 個位元。

- 使用 %I32x 可顯示十六進位格式的 32 位元整數類型。

- 使用 %I64x 顯示十六進位格式的 64 位元整數類型。

- %p (指標的十六進位格式) 在 64 位元 Windows 作業系統上將如預期運作。

如需詳細資訊，請參閱

- [MSVC 編譯器選項](reference/compiler-options.md)

- [移轉提示](/windows/win32/WinProg64/migration-tips)

## <a name="see-also"></a>另請參閱

[設定適用於 64 位元、x64 目標的 C++ 專案](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Visual C++ 移植和升級指南](../porting/visual-cpp-porting-and-upgrading-guide.md)
