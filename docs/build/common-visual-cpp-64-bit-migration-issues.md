---
title: Visual C++ 64 位元移轉時常見的問題
ms.date: 11/04/2016
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- upgrading Visual C++ applications, 32-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: 1eb5a7f8d708d16241f1637269f31563378f084d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468766"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Visual C++ 64 位元移轉時常見的問題

當您使用 Visual c++ 建立在 64 位元 Windows 作業系統上執行的應用程式時，您應注意下列問題：

- `int` 和 `long` 是 64 位元 Windows 作業系統上的 32 位元值。 對於您要為 64 位元平台進行編譯的程式，您應小心不要將指標指派給 32 位元變數。 指標在 64 位元平台上是 64 位元的，如果您將指標指派給 32 位元變數，將會截斷指標值。

- `size_t``time_t`，和`ptrdiff_t`是在 64 位元 Windows 作業系統上的 64 位元值。

- 在 32 位元 Windows 作業系統上，`time_t` 在 Visual C++ 2005 之前的 Visual C++ 版本中是 32 位元值。 `time_t` 現在預設為 64 位元整數。 如需詳細資訊，請參閱 <<c0> [ 時間管理](../c-runtime-library/time-management.md)。

   您應注意程式碼在何處取用 `int` 值，並將其視為 `size_t` 或 `time_t` 值來處理。 此數值可能會成長而大於 32 位元數值，且資料在傳回至 `int` 儲存體時將會截斷。

%x (十六進位 `int` 格式) `printf` 修飾詞在 64 位元 Windows 作業系統上將無法如預期運作。 它只會處理傳遞給它之值的前 32 個位元。

- 使用 %I32x 可顯示十六進位格式的 32 位元整數類型。

- 使用 %I64x 顯示十六進位格式的 64 位元整數類型。

- %p (指標的十六進位格式) 在 64 位元 Windows 作業系統上將如預期運作。

如需詳細資訊，請參閱:

- [編譯器選項](../build/reference/compiler-options.md)

- [移轉提示](/windows/desktop/WinProg64/migration-tips)

## <a name="see-also"></a>另請參閱

[針對 64 位元 x64 目標設定 Visual C++](../build/configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Visual C++ 移植和升級指南](../porting/visual-cpp-porting-and-upgrading-guide.md)