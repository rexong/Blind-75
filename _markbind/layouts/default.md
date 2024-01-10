<head-bottom>
  <link rel="stylesheet" href="{{baseUrl}}/stylesheets/main.css">
</head-bottom>

<header sticky>
  <navbar type="dark">
    <a slot="brand" href="{{baseUrl}}/index.html" title="Home" class="navbar-brand">Blind 75</a>
    <li slot="right">
      <form class="navbar-form">
        <searchbar :data="searchData" placeholder="Search" :on-hit="searchCallback" menu-align-right></searchbar>
      </form>
    </li>
  </navbar>
</header>

<div id="flex-body">
  <nav id="site-nav">
    <div class="site-nav-top">
      <div class="fw-bold mb-2" style="font-size: 1.25rem;">Contents</div>
    </div>
    <div class="nav-component slim-scroll">
      <site-nav>
* [Home :house:]({{ baseUrl }}/index.html)
* Arrays & Hashing 
  * [Contains Duplicate]({{ baseUrl }}/contents/arrays-and-hashing/contains-duplicate.html)
  * [Valid Anagram]({{ baseUrl }}/contents/arrays-and-hashing/valid-anagram.html)
  * [Two Sum]({{ baseUrl }}/contents/arrays-and-hashing/two-sum.html)
  * [Group Anagrams]({{ baseUrl }}/contents/arrays-and-hashing/group-anagrams.html)
  * [Top K Frequent Element]({{ baseUrl }}/contents/arrays-and-hashing/top-k-frequent-element.html)
  * [Product of Array Except Self]({{ baseUrl }}/contents/arrays-and-hashing/product-of-array-except-self.html)
  * [Longest Consecutive Sequence]({{ baseUrl }}/contents/arrays-and-hashing/longest-consecutive-sequence.html)
  * [String Encode and Decode]({{ baseUrl }}/contents/arrays-and-hashing/string-encode-and-decode.html)
* Stack
  * [Valid Parentheses]({{ baseUrl }}/contents/stack/valid-parentheses.html)
* Two Pointer
  * [Valid Palindrome]({{ baseUrl }}/contents/two-pointer/valid-palindrome.html)
  * [Container with Most Water]({{ baseUrl }}/contents/two-pointer/container-with-most-water.html)
  * [3Sum]({{ baseUrl }}/contents/two-pointer/3-sum.html)
* Sliding Window
  * [Best Time to Buy and Sell Stock]({{ baseUrl }}/contents/sliding-window/best-time-to-buy-and-sell-stock.html)
  * [Longest Substring without Repeating Characters]({{ baseUrl }}/contents/sliding-window/longest-substring-without-repeating-characters.html)
  * [Longest Repeating Character Replacement]({{ baseUrl }}/contents/sliding-window/longest-repeating-character-replacement.html)
* Binary Search
  * [Find Minimum in Rotated Sorted Array]({{ baseUrl }}/contents/binary-search/find-minimum-in-rotated-sorted-array.html)
  * [Search in Rotated Sorted Array]({{ baseUrl }}/contents/binary-search/search-in-rotated-sorted-array.html)
* Linked List
  * [Linked List Cycle]({{ baseUrl }}/contents/linked-list/linked-list-cycle.html)
  * [Merge Two Sorted Lists]({{ baseUrl }}/contents/linked-list/merge-two-sorted-lists.html)
  * [Reverse Linked List]({{ baseUrl }}/contents/linked-list/reverse-linked-list.html)
  * [Reorder List]({{ baseUrl }}/contents/linked-list/reorder-list.html)
  * [Remove Nth Node From End of List]({{ baseUrl }}/contents/linked-list/remove-nth-node-from-end-of-list.html)
* Trees
  * [Invert Binary Tree]({{ baseUrl }}/contents/trees/invert-binary-tree.html)
  * [Maximum Depth of Binary Tree]({{ baseUrl }}/contents/trees/maximum-depth-of-binary-tree.html)
  * [Same Tree]({{ baseUrl }}/contents/trees/same-tree.html)
  * [Subtree of Another Tree]({{ baseUrl }}/contents/trees/subtree-of-another-tree.html)
  * [Validate Binary Search Tree]({{ baseUrl }}/contents/trees/validate-binary-search-tree.html)
  * [Lowest Common Ancestor of a Binary Search Tree]({{ baseUrl }}/contents/trees/lowest-common-ancestor-of-a-binary-search-tree.html)
  * [Binary Tree Level Order Traversal]({{ baseUrl }}/contents/trees/binary-tree-level-order-traversal.html)
  * [Kth Smallest Element in a BST]({{ baseUrl }}/contents/trees/kth-smallest-element-in-a-bst.html)
  * [Construct Binary Tree from Preorder and Inorder Traversal]({{ baseUrl }}/contents/trees/construct-binary-tree-from-preorder-and-inorder-traversal.html)
* Tries
  * [Implement Trie (Prefix Tree)]({{ baseUrl }}/contents/tries/implement-trie.html)
  * [Design Add and Search Words Data Structure]({{ baseUrl }}/contents/tries/design-add-and-search-words-data-structure.html)
* Backtracking
  * [Combination Sum]({{ baseUrl }}/contents/backtracking/combination-sum.html)
  * [Word Search]({{ baseUrl }}/contents/backtracking/word-search.html)
* Graphs
  * [Number of Islands]({{ baseUrl }}/contents/graphs/number-of-islands.html)
  * [Clone Graph]({{ baseUrl }}/contents/graphs/clone-graph.html)
  * [Pacific Atlantic Water Flow]({{ baseUrl }}/contents/graphs/pacific-atlantic-water-flow.html)
  * [Course Schedule]({{ baseUrl }}/contents/graphs/course-schedule.html)
  * [Valid Graph]({{ baseUrl }}/contents/graphs/valid-tree.html)
  * [Count Connected Components]({{ baseUrl }}/contents/graphs/count-connected-components.html)
* Bit Manipulation
  * [Number of 1 Bits]({{ baseUrl }}/contents/bit-manipulation/number-of-1-bits.html)
  * [Counting Bits]({{ baseUrl }}/contents/bit-manipulation/counting-bits.html)
  * [Reverse Bits]({{ baseUrl }}/contents/bit-manipulation/reverse-bits.html)
  * [Missing Number]({{ baseUrl }}/contents/bit-manipulation/missing-number.html)
  * [Sum of Two Integers]({{ baseUrl }}/contents/bit-manipulation/sum-of-two-integers.html)
* Math & Geometry
  * [Rotate Image]({{ baseUrl }}/contents/math-and-geometry/rotate-image.html)
  * [Spiral Matrix]({{ baseUrl }}/contents/math-and-geometry/spiral-matrix.html)
  * [Set Matrix Zeroes]({{ baseUrl }}/contents/math-and-geometry/set-matrix-zeroes.html)
* Dynamic Programing
  * [Climbing Stairs]({{ baseUrl }}/contents/dynamic-programming/climbing-stairs.html)
  * [House Robber]({{ baseUrl }}/contents/dynamic-programming/house-robber.html)
  * [House Robber II]({{ baseUrl }}/contents/dynamic-programming/house-robber-ii.html)
  * [Longest Palindromic Substring]({{ baseUrl }}/contents/dynamic-programming/longest-palindromic-substring.html)
  * [Palindromic Substrings]({{ baseUrl }}/contents/dynamic-programming/palindromic-substrings.html)
  * [Coin Change]({{ baseUrl }}/contents/dynamic-programming/coin-change.html)
  * [Decode Ways]({{ baseUrl }}/contents/dynamic-programming/decode-ways.html)
  * [Maximum Product Subarray]({{ baseUrl }}/contents/dynamic-programming/maximum-product-subarray.html)
  * [Word Break]({{ baseUrl }}/contents/dynamic-programming/word-break.html)
  * [Longest Increasing Subsequence]({{ baseUrl }}/contents/dynamic-programming/longest-increasing-subsequence.html)
  * [Unique Paths]({{ baseUrl }}/contents/dynamic-programming/unique-paths.html)
  * [Longest Common Subsequence]({{ baseUrl }}/contents/dynamic-programming/longest-common-subsequence.html)
* Intervals
  * [Meeting Schedule]({{ baseUrl }}/contents/intervals/meeting-schedule.html)
  * [Meeting Schedule II]({{ baseUrl }}/contents/intervals/meeting-schedule-ii.html)
  * [Merge Intervals]({{ baseUrl }}/contents/intervals/merge-intervals.html)
  * [Non-overlapping Intervals]({{ baseUrl }}/contents/intervals/non-overlapping-intervals.html) 
      </site-nav>
    </div>
  </nav>
  <div id="content-wrapper">
    <breadcrumb />
    {{ content }}
  </div>
  <nav id="page-nav">
    <div class="nav-component slim-scroll">
      <page-nav />
    </div>
  </nav>
  <scroll-top-button></scroll-top-button>
</div>

<footer>
  <!-- Support MarkBind by including a link to us on your landing page! -->
  <div class="text-center">
    <small>[Generated by {{MarkBind}}]</small>
  </div>
</footer>
