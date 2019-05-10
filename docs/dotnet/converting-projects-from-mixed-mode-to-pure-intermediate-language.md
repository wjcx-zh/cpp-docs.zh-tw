---
title: 將專案從混合模式轉換為純中繼語言
ms.date: 11/04/2016
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 2f63b6860157e315d44f7c050812a7f0b97f2726
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448050"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>將專案從混合模式轉換為純中繼語言

所有 Visual C++ CLR 專案連結到 C 執行階段程式庫預設值。 因此，這些專案分類為混合式應用程式，因為它們結合以 common language runtime （managed 程式碼） 為目標的程式碼的原生程式碼。 在編譯時它們會編譯成中繼語言 (IL)，也稱為 Microsoft intermediate language (MSIL)。

> [!IMPORTANT]
> 已被取代的 visual Studio 2015 和 Visual Studio 2017 不再支援建立 **/clr: pure**或是 **/clr: safe** CLR 應用程式程式碼。 如果您需要純或安全的組件時，我們建議您將轉譯成 C# 應用程式。

如果您使用較早版本的 MicrosoftC++支援的編譯器工具組 **/clr: pure**或 **/clr: safe**，您可以使用此程序轉換為純 MSIL 的程式碼：

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>若要將您的混合式應用程式轉換成純中繼語言

1. 移除連結[C 執行階段程式庫](../c-runtime-library/crt-library-features.md)(CRT):

   1. 在.cpp 檔案中定義您的應用程式的進入點變更的進入點`Main()`。 使用`Main()`指出您的專案不會連結到 CRT。

   2. 在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取**屬性**的捷徑功能表，開啟您的應用程式的屬性頁上。

   3. 在**進階**專案屬性頁**連結器**，選取**進入點**，然後輸入**Main**在此欄位中。

   4. 主控台應用程式，在**系統**專案屬性頁**連結器**，選取**子系統**欄位，然後變更為**主控台 （/SUBSYSTEM:CONSOLE)**。

      > [!NOTE]
      > 您沒有設定這個屬性，Windows Forms 應用程式，因為**子系統**欄位設定為**Windows (/ 子系統： WINDOWS)** 預設。

   5. 在 stdafx.h 中標記為註解所有`#include`陳述式。 例如，在主控台應用程式：

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       -或-

       例如，在 Windows Forms 應用程式：

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. 針對 Windows Forms 應用程式，在 Form1.cpp，標記為註解`#include`參考 windows.h 陳述式。 例如：

      ```cpp
      // #include <windows.h>
      ```

2. 將下列程式碼新增至 stdafx.h 中：

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. 移除所有的非受控型別：

   只要適當地取代未受管理的類型結構的參考[系統](/dotnet/api/system)命名空間。 下表列出常見 managed 型別：

   |結構|描述|
   |---------------|-----------------|
   |[布林值](/dotnet/api/system.boolean)|表示布林值。|
   |[Byte](/dotnet/api/system.byte)|代表 8 位元不帶正負號的整數。|
   |[Char](/dotnet/api/system.char)|代表 Unicode 字元。|
   |[DateTime](/dotnet/api/system.datetime)|表示時間的瞬間，通常以一天的日期和時間表示。|
   |[Decimal](/dotnet/api/system.decimal)|代表十進位數值。|
   |[Double](/dotnet/api/system.double)|表示雙精度浮點數。|
   |[Guid](/dotnet/api/system.guid)|表示全域唯一識別項 (GUID)。|
   |[Int16](/dotnet/api/system.int16)|表示 16 位元帶正負號的整數。|
   |[Int32](/dotnet/api/system.int32)|表示 32 位元帶正負號的整數。|
   |[Int64](/dotnet/api/system.int64)|表示 64 位元帶正負號的整數。|
   |[IntPtr](/dotnet/api/system.intptr)|平台專用的類型，用以代表指標或控點。|
   |[SByte](/dotnet/api/system.byte)|代表 8 位元帶正負號的整數。|
   |[Single](/dotnet/api/system.single)|表示單精確度浮點數。|
   |[TimeSpan](/dotnet/api/system.timespan)|表示時間間隔。|
   |[UInt16](/dotnet/api/system.uint16)|表示 16 位元不帶正負號的整數 (Unsigned Integer)。|
   |[UInt32](/dotnet/api/system.uint32)|表示 32 位元不帶正負號的整數 (Unsigned Integer)。|
   |[UInt64](/dotnet/api/system.uint64)|表示 64 位元不帶正負號的整數 (Unsigned Integer)。|
   |[UIntPtr](/dotnet/api/system.uintptr)|平台專用的類型，用以代表指標或控點。|
   |[Void](/dotnet/api/system.void)|表示不會傳回值的方法也就是方法具有 void 傳回型別。|