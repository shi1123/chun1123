---
title: java的equals引发的血案
date: '2021/9/29 02:34:07'
description: 使用 == 对 Integer 进行数值判断导致的bug
tags:
  - java
  - leetcode
  - Integer
  - equals
  - 滑动窗口
  - 子串
categories:
  - 编程人生
  - 后端
  - java
  - Java语法
---


记一次 .equals 引起的bug

#### [76. 最小覆盖子串](https://leetcode-cn.com/problems/minimum-window-substring/)

难度困难1356

给你一个字符串 `s` 、一个字符串 `t` 。返回 `s` 中涵盖 `t` 所有字符的最小子串。如果 `s` 中不存在涵盖 `t` 所有字符的子串，则返回空字符串 `""` 。

 

**注意：**

- 对于 `t` 中重复字符，我们寻找的子字符串中该字符数量必须不少于 `t` 中该字符数量。
- 如果 `s` 中存在这样的子串，我们保证它是唯一的答案。



```
public class Solution{
    public String minWindow(String s, String t) {
        Map<Character, Integer> window = new HashMap<>();
        Map<Character, Integer> need = new HashMap<>();
        int valid = 0;
        int left=0,right=0;
        int start = 0,len = Integer.MAX_VALUE;

        for(char c : t.toCharArray()){
            need.put(c, need.getOrDefault(c, 0)+1);
        }

        while(right < s.length()) {
            char c = s.charAt(right);
            right++;
            window.put(c, window.getOrDefault(c, 0)+1);
            if(need.containsKey(c)){
            // 这里如果使用 == 判断，则会出错
                if(need.get(c).equals(window.get(c))){
                    valid++;
                }
            }

            while(valid == need.size()){
                if(right -left < len){
                    start = left;
                    len = right - left;
                }
                char d = s.charAt(left);
                left++;
                if(need.containsKey(d)){
                // 这里如果使用 == 判断，则会出错
                    if(window.get(d).equals(need.get(d))){
                        valid--;
                    }
                }
                window.put(d, window.get(d) - 1);
            }
        }
        return len == Integer.MAX_VALUE ? "" : s.substring(start, start+len);
    }
}
```



在s和t为超大的字符串的 时候，存放在map中的Integer 已经超过128的范围，这时候，就回 new 出新的对象，这时候使用== 判断，则会不一样。导致测试用例不能通过。