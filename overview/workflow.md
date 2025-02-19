[edit]()

# WIP Workflow
1. Review Items
2. Actionalble
3. Process
4. Project

   [![](https://mermaid.ink/img/pako:eNplklFPwjAQx7_KpU-QsJj4SAwGmBAfVAJ7UWbI0d2gsvWWrhMN47vbdZNI7ENz_f9_17u0dxKSExJDkWZ8lHs0FqIw1uDWpNdb0qei493W3IweLeVlv99ZEAQjmJ7G0irWuM3owsD9uWWmDVNvNs8vm413iwxlyynH1TBbpzhMMbAGyz1Eze7dgE3gg1VBsrIZNjWunTZxy3yAJaVkSEt6vy77-rDq6k4NoSVoe60hXC8MSyrLS8tdZugzC8MfJK03LZaHGuZNQqNB5M6wyLDtZlyWaqfBMnT-1T0Je0jzsYZoHTIoDbeQK91Rc09p-rI1TFpp9l-KvJSiylwff6ULFWsxEDmZHFXivvHUQLGwe8opFkMXJpRildlYxPrsUKwsr761FENrKhoIw9VuL9xzZqU7VUXi3ipUuDOY_yIF6jfm_AJRoiybp3Zu_PicfwCbpb1p?type=png)](https://mermaid.live/edit#pako:eNplklFPwjAQx7_KpU-QsJj4SAwGmBAfVAJ7UWbI0d2gsvWWrhMN47vbdZNI7ENz_f9_17u0dxKSExJDkWZ8lHs0FqIw1uDWpNdb0qei493W3IweLeVlv99ZEAQjmJ7G0irWuM3owsD9uWWmDVNvNs8vm413iwxlyynH1TBbpzhMMbAGyz1Eze7dgE3gg1VBsrIZNjWunTZxy3yAJaVkSEt6vy77-rDq6k4NoSVoe60hXC8MSyrLS8tdZugzC8MfJK03LZaHGuZNQqNB5M6wyLDtZlyWaqfBMnT-1T0Je0jzsYZoHTIoDbeQK91Rc09p-rI1TFpp9l-KvJSiylwff6ULFWsxEDmZHFXivvHUQLGwe8opFkMXJpRildlYxPrsUKwsr761FENrKhoIw9VuL9xzZqU7VUXi3ipUuDOY_yIF6jfm_AJRoiybp3Zu_PicfwCbpb1p)
   
```mermaid
flowchart TD
    B((Review<br/>Items))
    B --> C{Actionable<br/>Item ?}
    C -->|__NO__<br/>place<br/>item| F[fa:fa-trash Trash<br/>-or-<br/>Specutlation<br/>-or-<br/>fa:fa-book Reference]
    C -->|__YES__<br/>Create Action| D[Process<br/>Item]
    D -->|project<br/>task| G[Project Task Plan<br/>Assign to Project]
    D -->|do<br/>now| T[Do in 2 min]
    G -->|next| B
    F -->|next| B
    T -->|fail| G
    T -->|next| B
```
