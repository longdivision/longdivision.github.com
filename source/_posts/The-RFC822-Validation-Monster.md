---
title: The RFC822 Validation Monster
date: 2012-11-08 00:00:00
tags:
---
I recently saw the [RFC822 valid email address regex][1] again, raised on a [Hacker News post][2]. It's enormous - too long to make any sense of. Here are the first 3 lines (of 82):

``` perl
(?:(?:\r\n)?[ \t])*(?:(?:(?:[^()<>@,;:\\".\[\] \000-\031]+(?:(?:(?:\r\n)?[ \t]
)+|\Z|(?=[\["()<>@,;:\\".\[\]]))|"(?:[^\"\r\\]|\\.|(?:(?:\r\n)?[ \t]))*"(?:(?:
\r\n)?[ \t])*)(?:\.(?:(?:\r\n)?[ \t])*(?:[^()<>@,;:\\".\[\] \000-\031]+(?:(?:(
```

Validating email addresses has always been a pain and there is no perfect solution. Even if you were to pass the above validation, there's no guarantee the provided address actually exists.

Fortunately there was some good advice for the sanest way to deal with addresses. To summarise:

* The only way to know if an email is valid is to send one.
* There is a [recommended regex][3] in the HTML5 spec.
* A really simple approach is check for a character either side of an @ before sending an email.
To get an idea of the kinds of addresses which lead to such a monstrous regex, check out [this list][7].

Credit to [Jabbles][4], [3ds 37][5] and [meaty][6] for raising the above points.

[1]: http://www.ex-parrot.com/~pdw/Mail-RFC822-Address.html
[2]: https://news.ycombinator.com/item?id=4793353
[3]: http://www.whatwg.org/specs/web-apps/current-work/multipage/forms.html#valid-e-mail-address
[4]: https://news.ycombinator.com/item?id=4793498
[5]: https://news.ycombinator.com/item?id=4793627
[6]: https://news.ycombinator.com/item?id=4793504
[7]: https://web.archive.org/web/20120830115453/http://isemail.info/_system/is_email/test/?all
