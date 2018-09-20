---
title: 規則運算式 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular expressions [C++]
- .NET Framework [C++], regular expressions
- regular expressions [C++], about regular expressions
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
- substrings, simple matches
- searching, exact substring matches
- strings [C++], exact substring matching
- regular expressions [C++], simple matching
- IsMatch method
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
- regular expressions [C++], rearranging data
- data [C++], rearranging
- search and replace
- Replace method
- regular expressions [C++], search and replace
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 838bab49-0dbc-4089-a604-ef146269ef5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7f9937d9f93af6179d890f1e9160dd8900cd9f14
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375611"
---
# <a name="regular-expressions-ccli"></a>規則運算式 (C++/CLI)

示範如何使用.NET Framework 中的規則運算式類別的各種字串作業。

下列主題示範如何使用.NET Framework<xref:System.Text.RegularExpressions>命名空間 (並在其中一個案例<xref:System.String.Split%2A?displayProperty=fullName>方法) 來搜尋、 剖析和修改字串。

## <a name="parse_regex"></a> 使用規則運算式剖析字串

下列程式碼範例示範簡單的字串剖析使用<xref:System.Text.RegularExpressions.Regex>類別中<xref:System.Text.RegularExpressions?displayProperty=fullName>命名空間。 會建構包含多種類型的文字分隔符號的字串。 使用再剖析字串<xref:System.Text.RegularExpressions.Regex>類別搭配<xref:System.Text.RegularExpressions.Match>類別。 然後，會個別顯示每個單字的句子。

### <a name="example"></a>範例

```cpp
// regex_parse.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main( )
{
   int words = 0;
   String^ pattern = "[a-zA-Z]*";
   Console::WriteLine( "pattern : '{0}'", pattern );
   Regex^ regex = gcnew Regex( pattern );

   String^ line = "one\ttwo three:four,five six  seven";
   Console::WriteLine( "text : '{0}'", line );
   for( Match^ match = regex->Match( line );
        match->Success; match = match->NextMatch( ) )
   {
      if( match->Value->Length > 0 )
      {
         words++;
         Console::WriteLine( "{0}", match->Value );
      }
   }
   Console::WriteLine( "Number of Words : {0}", words );

   return 0;
}
```

## <a name="parse_split"></a> 使用 Split 方法剖析字串

下列程式碼範例示範如何使用<xref:System.String.Split%2A?displayProperty=fullName>方法，以從字串擷取每個字。 字串，包含多種類型的文字分隔符號是建構和剖析藉由呼叫<xref:System.String.Split%2A>分隔符號的清單。 然後，會個別顯示每個單字的句子。

### <a name="example"></a>範例

```cpp
// regex_split.cpp
// compile with: /clr
using namespace System;

int main()
{
   String^ delimStr = " ,.:\t";
   Console::WriteLine( "delimiter : '{0}'", delimStr );
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ words;
   String^ line = "one\ttwo three:four,five six seven";

   Console::WriteLine( "text : '{0}'", line );
   words = line->Split( delimiter );
   Console::WriteLine( "Number of Words : {0}", words->Length );
   for (int word=0; word<words->Length; word++)
      Console::WriteLine( "{0}", words[word] );

   return 0;
}
```

## <a name="regex_simple"></a> 使用規則運算式進行簡單對應

下列程式碼範例會使用規則運算式來尋找確切的子字串相符項目。 搜尋由靜態<xref:System.Text.RegularExpressions.Regex.IsMatch%2A>方法，這個方法會採用兩個字串做為輸入。 第一個是要搜尋的字串和第二個是要搜尋的模式。

### <a name="example"></a>範例

```cpp
// regex_simple.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
   array<String^>^ sentence =
   {
      "cow over the moon",
      "Betsy the Cow",
      "cowering in the corner",
      "no match here"
   };

   String^ matchStr = "cow";
   for (int i=0; i<sentence->Length; i++)
   {
      Console::Write( "{0,24}", sentence[i] );
      if ( Regex::IsMatch( sentence[i], matchStr,
                     RegexOptions::IgnoreCase ) )
         Console::WriteLine("  (match for '{0}' found)", matchStr);
      else
         Console::WriteLine("");
   }
   return 0;
}
```

## <a name="regex_extract"></a> 使用規則運算式來擷取資料欄位

下列程式碼範例示範如何從格式化字串中擷取資料的規則運算式的使用。 下列程式碼範例使用<xref:System.Text.RegularExpressions.Regex>類別，以指定的電子郵件地址對應的模式。 這個模式會包含可用來擷取使用者和主機名稱部分，每個電子郵件地址的欄位識別碼。 <xref:System.Text.RegularExpressions.Match>類別用來執行實際的模式比對。 如果指定的電子郵件地址是有效的會擷取並顯示的使用者名稱和主機名稱。

### <a name="example"></a>範例

```cpp
// Regex_extract.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
    array<String^>^ address=
    {
        "jay@southridgevideo.com",
        "barry@adatum.com",
        "treyresearch.net",
        "karen@proseware.com"
    };

    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");

    for (int i=0; i<address->Length; i++)
    {
        Match^ m = emailregex->Match( address[i] );
        Console::Write("\n{0,25}", address[i]);

        if ( m->Success )
        {
            Console::Write("   User='{0}'",
            m->Groups["user"]->Value);
            Console::Write("   Host='{0}'",
            m->Groups["host"]->Value);
        }
        else
            Console::Write("   (invalid email address)");
        }

    Console::WriteLine("");
    return 0;
}
```

## <a name="regex_rearrange"></a> 使用規則運算式重新整理資料

下列程式碼範例示範如何使用.NET Framework 規則運算式支援，以重新排列或重新格式化資料。 下列程式碼範例會使用<xref:System.Text.RegularExpressions.Regex>和<xref:System.Text.RegularExpressions.Match>類別以從字串中擷取第一個和最後一個名稱，並以反向順序顯示這些名稱項目。

<xref:System.Text.RegularExpressions.Regex>類別用來建構描述目前的資料格式的規則運算式。 這兩個名稱會假設為以逗號分隔，而且可以使用任何數量的逗號周圍的空白。 <xref:System.Text.RegularExpressions.Match>方法可用來分析每個字串。 如果成功，會從擷取名字和姓氏<xref:System.Text.RegularExpressions.Match>物件，並顯示。

### <a name="example"></a>範例

```cpp
// regex_reorder.cpp
// compile with: /clr
#using <System.dll>
using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ name =
   {
      "Abolrous, Sam",
      "Berg,Matt",
      "Berry , Jo",
      "www.contoso.com"
   };

   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");

   for ( int i=0; i < name->Length; i++ )
   {
      Console::Write( "{0,-20}", name[i] );
      Match^ m = reg->Match( name[i] );
      if ( m->Success )
      {
         String^ first = m->Groups["first"]->Value;
         String^ last = m->Groups["last"]->Value;
         Console::WriteLine("{0} {1}", first, last);
      }
      else
         Console::WriteLine("(invalid)");
   }
   return 0;
}
```

## <a name="regex_search"></a> 使用規則運算式進行搜尋和取代

下列程式碼範例示範如何規則運算式類別<xref:System.Text.RegularExpressions.Regex>可用來執行搜尋和取代。 做法是使用<xref:System.Text.RegularExpressions.Regex.Replace%2A>方法。 使用的版本會採用兩個字串做為輸入： 修改字串和要插入取代的區段 （如果有的話） 的字串，符合模式提供給<xref:System.Text.RegularExpressions.Regex>物件。

此程式碼會以底線 (_) 取代字串中的所有數字，然後再取代具有空字串，以便有效地移除它們。 相同的效果，即可在單一步驟中，但兩個步驟這裡基於示範用途使用。

### <a name="example"></a>範例

```cpp
// regex_replace.cpp
// compile with: /clr
#using <System.dll>
using namespace System::Text::RegularExpressions;
using namespace System;

int main()
{
   String^ before = "The q43uick bro254wn f0ox ju4mped";
   Console::WriteLine("original  : {0}", before);

   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");
   String^ after = digitRegex->Replace(before, "_");
   Console::WriteLine("1st regex : {0}", after);

   Regex^ underbarRegex = gcnew Regex("_");
   String^ after2 = underbarRegex->Replace(after, "");
   Console::WriteLine("2nd regex : {0}", after2);

   return 0;
}
```

## <a name="regex_validate"></a> 使用規則運算式驗證資料格式

下列程式碼範例示範如何使用規則運算式來驗證字串的格式。 在下列程式碼範例中，字串應該包含有效的電話號碼。 下列程式碼範例會使用字串"\d{3}-\d{3}-\d{4}"來指出每個欄位代表有效的電話號碼。 在字串中的"d"表示數字，和"d"後面的引數指出必須要有的數字數目。 在此情況下，數字，才能以連字號分隔。

### <a name="example"></a>範例

```cpp
// regex_validate.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ number =
   {
      "123-456-7890",
      "444-234-22450",
      "690-203-6578",
      "146-893-232",
      "146-839-2322",
      "4007-295-1111",
      "407-295-1111",
      "407-2-5555",
   };

   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";

   for ( int i = 0; i < number->Length; i++ )
   {
      Console::Write( "{0,14}", number[i] );

      if ( Regex::IsMatch( number[i], regStr ) )
         Console::WriteLine(" - valid");
      else
         Console::WriteLine(" - invalid");
   }
   return 0;
}
```

## <a name="related-sections"></a>相關章節

[.NET Framework 規則運算式](/dotnet/standard/base-types/regular-expressions)

## <a name="see-also"></a>另請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)