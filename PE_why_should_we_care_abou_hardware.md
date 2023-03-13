### Why Should We Care About Hardware As Software Engineer ?


To start with this series, lets answer the question : " Why should we care about hardwares ?"

- **We have taught for so many years that software is independant of hardware, and that's simply not true.** When I began learning how to optimize programs myself, one big mistake I made was to rely primarily on the empirical approach. Not understanding how computers really worked, I would semi-randomly swap nested loops, rearrange arithmetic, combine branch conditions, inline functions by hand, and follow all sorts of other performance tips I’ve heard from other people, `blindly hoping for improvement`.

- The second lie is that code should be designed around them all of the world that you should have this model of how the world works and **you should telling the story inside your code and ignoring the realities the both the hardware and the data.**  Yes, that's how software engineer think about the world via Object Oriented Design and Domain Driven Design and it's an other missconception ( or it's a tradeoff between OOD-DOD ). 
  
  [1] : [Mike Acton about two misconceptions](https://youtu.be/u8B3j8rqYMw?t=307)
   
   **In the world of Performance Engineering** like : Database, Computational Engine,Game Engine, Audio Software industry and the last but not least High Performance Trading, people really really care about the underlying hardware their code being running on. The Data Oriented Design and approaches to make full use of Modern Hardware like avoid branch miss prediction, cache friendly coding and taking advantages of SIMD instructions with vectorization are highly adopted. 

You may not get familiar with those concepts for now, take a deep breath and step by step go through this series to learn about how Modern Hardware works and affects to the performance.
You will learn about something like:

- Log2n binary search of sorted array can beat O(1)  searches of heap-base hash tables.
- Asymptotic complexity is not the sole deciding factor anymore, micro benchmarking rule them all. 
- 5x faster hash tables ( compare to std::unordered_map ). 
- How to implement some algorithms with SIMD-thinking
- and ect.

It would have probably saved me dozens, if not hundreds of hours of going no where with performance chasing if I learned computer architecture _before_ doing algorithmic programming. And the closing idea for the series preface is the main idea from [MonetDbX100 paper](https://www.cidrdb.org/cidr2005/papers/P19.pdf):
" The more human friendly your code is, the more harmful it makes to the CPU ". 

Next Topics:
- [A Tour Of Modern Hardware](PE_a_tour_of_modern_hardware.md)
- [Cache Effect On Performance](PE_cache_effect_on_performance.md)
- [Data Oriented Design](PE_data_oriented_design.md)
- [SIMD Mini Series](PE_SIMD_mini_series.md)
