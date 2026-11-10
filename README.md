# Static Program Slicing with Java Dependence Graphs

A Java static-analysis project exploring how control and data relationships can identify the statements relevant to a slicing criterion. The repository contains an initial slicing implementation and a graph-oriented evolution organized around explicit dependence models.

## Analysis architecture

```text
Java source → Eclipse JDT compilation unit
                         |
              ┌──────────┴──────────┐
       Control dependence     Data dependence
              |                      |
          Graph nodes and dependence exploration
```

## Implementations

**`ProgramSlicing/`** contains the initial analyzer under `src/othersPackage`, including graph nodes and the operation driver.

**`SlicingFinal/`** organizes the implemented graph analysis into `controlDependence`, `dataDependence`, and `graph` packages. `mainPackage.Operation` demonstrates parsing and traversal of a control-dependence graph. Eclipse JDT visitors process the Java syntax tree and populate the project's graph structures.

The separation of syntactic traversal from dependence representation makes the analysis stages visible and provides a useful view of how static slicing is constructed.

## Explore and run

Use a JDK and import either implementation as an independent Java project. Mark its `src/` directory as the source root and add its supplied `lib/` JARs to the runtime classpath. Run `mainPackage.MainClass` from the selected project directory.

Read the corresponding `Operation` class for the source-file location and criterion used by that driver. Follow a sample statement from the parsed compilation unit through its graph nodes to inspect how dependence traversal selects relevant statements.

## Technologies and contributions

Java, Eclipse JDT ASTParser, AST visitors, graph nodes, control/data dependence modeling, and traversal-based slicing form the technical core. The two implementations preserve the progression from a combined analyzer toward a package structure aligned with the analysis pipeline.
