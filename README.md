Notes on the paper [L. Damas, R. Milner - Principal type-schemes for functional programs](http://steshaw.org/hm/milner-damas.pdf) [Damas 1982]

- The paper is based on *polymorphic type discipline* of [ML](http://www.cs.unc.edu/~stotts/144/ML/).
- Aims to show that the *type assignment algorithm* in [Milner 1978]:
  - Finds the **most general type possible**, for every *expression* and *declaration*.

Finding the most general type possible allows:

- **Flexibility** (from polymoriphism), and
- **Robustness** (from semantic soundness), and
- **Detection of errors at compile time**.

## References

**[Damas 1982]** Damas, L. and Milner, R. 1982. Principal type-schemes for functional programs. *Proceedings of the 9th ACM SIGPLAN-SIGACT symposium on Principles of programming languages - POPL 82*(1982). DOI:http://dx.doi.org/10.1145/582153.582176.

**[Milner 1978]** Milner, R., 1978. A theory of type polymorphism in programming. *Journal of Computer and System Sciences*, 17(3), pp.348-375.

