## Blue Type Design Rules (Generic)

Use these conventions when adding or editing `.blue` types across the repository.

- Reserved fields
  - Do not define data fields named `name` or `description`. These are reserved by the Blue language for document/type metadata.
  - It is fine to use `description:` as schema metadata for fields (to explain them), but not as a declared data field within your data model.

- Referencing types
  - Prefer referencing named types via `type: <TypeName>` over large inline shapes.
  - Create small, reusable named types to keep schemas readable and composable.

- Collections
  - Dictionary (map):
    - `type: Dictionary`
    - `keyType: <ScalarType>` (commonly `Text`)
    - `valueType: <TypeName>` (prefer a named type)
  - List (array):
    - `type: List`
    - `itemType: <TypeName>`
  - Keep collection element types simple and well-documented.

- Polymorphism and type hierarchies
  - Use a small abstract/base type when several variants share common fields.
  - Each instance specifies its concrete `type` (no separate discriminator field is needed).
  - Keep base types minimal; add variant-specific fields only in concrete types.

- Constraints and validation
  - Use `constraints.options` for small closed sets of allowed values.
  - Keep strict validation light at the type level; heavy validation belongs in processors or UI.

- Field naming and clarity
  - Use clear, descriptive field names; avoid overloading short or ambiguous names.
  - Prefer using `Text` for identifiers and display strings; document the meaning in `description` metadata.
  - Document units and formats (e.g., milliseconds, ISO strings) in `description`.

- Style and formatting
  - Preserve existing indentation and formatting; match the surrounding style in the file.
  - Favor small, named types and multi-line formatting for readability over dense inline schemas.

- Examples
  - Dictionary type
    ```
    name: Widget Index
    type: Dictionary
    keyType: Text
    valueType: Widget
    ```
  - List field within a type
    ```
    name: Batch Operation
    steps:
      type: List
      itemType: Sequential Workflow Step
    ```


