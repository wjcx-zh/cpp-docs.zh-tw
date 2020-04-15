---
title: 使用 Managed 例外狀況中的基本概念
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: 6bc1e9c6d40599ae9a821179dcf56dbb7e21bf10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372520"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>使用 Managed 例外狀況中的基本概念

本主題討論託管應用程式中的異常處理。 也就是說,使用 **/clr**編譯器選項編譯的應用程式。

## <a name="in-this-topic"></a>本主題內容

- [在 /clr 下引發異常](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [CLR 延伸的嘗試/擷取區塊](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>備註

如果使用 **/clr**選項進行編譯,則可以處理 CLR<xref:System.Exception>異常以及標準 類提供了許多用於處理 CLR 異常的有用方法,建議作為使用者定義的異常類的基類。

**在 /clr**下不支援捕獲從介面派生的異常類型。 此外,通用語言運行時不允許捕獲堆疊溢出異常;堆疊溢出異常將終止進程。

有關託管和非託管應用程式中異常處理差異的詳細資訊,請參閱[C++ 的「託管擴展下異常處理行為差異](../dotnet/differences-in-exception-handling-behavior-under-clr.md)」。。

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>在 /clr 下引發異常

C++引發運算式將擴展以將句柄扔到 CLR 類型。 下面的範例建立自訂異常類型,然後引發該類型的實例:

```cpp
// clr_exception_handling.cpp
// compile with: /clr /c
ref struct MyStruct: public System::Exception {
public:
   int i;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   throw pMyStruct;
}
```

在引發之前,必須裝箱值類型:

```cpp
// clr_exception_handling_2.cpp
// compile with: /clr /c
value struct MyValueStruct {
   int i;
};

void GlobalFunction() {
   MyValueStruct v = {11};
   throw (MyValueStruct ^)v;
}
```

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>CLR 延伸的嘗試/擷取區塊

相同的**try**/**catch**塊結構可用於捕捉 CLR 和本機異常:

```cpp
// clr_exception_handling_3.cpp
// compile with: /clr
using namespace System;
ref struct MyStruct : public Exception {
public:
   int i;
};

struct CMyClass {
public:
   double d;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   pMyStruct->i = 11;
   throw pMyStruct;
}

void GlobalFunction2() {
   CMyClass c = {2.0};
   throw c;
}

int main() {
   for ( int i = 1; i >= 0; --i ) {
      try {
         if ( i == 1 )
            GlobalFunction2();
         if ( i == 0 )
            GlobalFunction();
      }
      catch ( CMyClass& catchC ) {
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );
         Console::WriteLine( catchC.d );
      }
      catch ( MyStruct^ catchException ) {
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );
         Console::WriteLine( catchException->i );
      }
   }
}
```

### <a name="output"></a>輸出

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>C++物件的展開順序

對於具有析構函數的任何C++對象,這些物件可能在引發函數和處理函數之間的運行時堆疊上。 由於 CLR 類型在堆上分配,因此展開不適用於它們。

引發異常的事件順序如下:

1. 運行時遍網查找適當的 catch 子句,或者對於 SEH(SEH 的篩選器除外)的情況,則運行以捕獲異常。 先按詞法順序搜索 Catch 子句,然後動態向下調用堆疊。

1. 找到正確的處理程式后,堆疊將解纏到該點。 對於堆疊上的每個函數調用,其本地物件都會被破壞,並且__finally塊從大多數嵌套向外執行。

1. 解包后,將執行 catch 子句。

### <a name="catching-unmanaged-types"></a>捕捉非託管類型

引發非託管物件類型時,將用類型<xref:System.Runtime.InteropServices.SEHException>的異常包裝它。 搜索適當的 CATCH 子**句**時,有兩種可能性。

- 如果遇到本機C++類型,則取消包裝異常,並將其與遇到的類型進行比較。 此比較允許以正常方式捕獲本機C++類型。

- 但是,如果首先檢查**SEHException**類型或其任何基類的**catch**子句,則子句將截取異常。 因此,應首先將捕獲本機C++類型的所有 catch 子句放在 CLR 類型的任何 catch 子句之前。

請注意

```
catch(Object^)
```

和

```
catch(...)
```

都會捕獲任何引發類型,包括 SEH 異常。

如果非託管類型被 catch(Object_)捕獲,則不會破壞引發的物件。

在引發或擷取非託管異常時,我們建議您使用[/EHsc](../build/reference/eh-exception-handling-model.md)編譯器選項而不是 **/EHs**或 **/EHa**。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)
