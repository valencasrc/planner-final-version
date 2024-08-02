# planner-final-version
Esta aplicação tem como objetivo ajudar na organização de viagens, permitindo a criação de eventos, a gestão de participantes, atividades e links relacionados.

### 📂 Estrutura do Projeto

1. **Participant**
   - **ParticipantRepository.java**: Interface para operações CRUD com a entidade `Participant`.
   - **ParticipantData.java**: Record que representa os dados de um participante.
   - **ParticipantCreateResponse.java**: Record que representa a resposta da criação de um participante.
   - **ParticipantController.java**: Controller responsável pelas operações relacionadas aos participantes.

2. **Trip**
   - **Trip.java**: Entidade que representa uma viagem.
   - **TripRequestPayload.java**: Record que representa os dados necessários para criar ou atualizar uma viagem.
   - **TripRepository.java**: Interface para operações CRUD com a entidade `Trip`.
   - **TripCreateResponse.java**: Record que representa a resposta da criação de uma viagem.
   - **TripController.java**: Controller responsável pelas operações relacionadas às viagens.

3. **Application**
   - **PlannerApplication.java**: Classe principal que inicia a aplicação Spring Boot.

### 🚀 Funcionalidades Principais

- **Gerenciamento de Viagens**
  - Criação de viagens com destino, data de início e fim, e informações do proprietário.
  - Atualização e confirmação de viagens.
  - Consulta de detalhes das viagens.

- **Gerenciamento de Participantes**
  - Convite de participantes para eventos.
  - Confirmação de participação.
  - Listagem de todos os participantes de uma viagem.

- **Gerenciamento de Atividades e Links**
  - Registro de atividades e links relacionados a uma viagem.
  - Listagem de todas as atividades e links de uma viagem.

### 🛠️ Tecnologias Utilizadas

- **Java**
- **Spring Boot**
- **Spring Data JPA**
- **Lombok**
- **Jakarta Persistence API**

### 📜 Código de Exemplo

Aqui está um exemplo de como a aplicação gerencia a confirmação de um participante:

```java
@RestController
@RequestMapping("/participants")
public class ParticipantController {

    @Autowired
    private ParticipantRepository repository;

    @PostMapping("/{id}/confirm")
    public ResponseEntity<Participant> confirmParticipant(@PathVariable UUID id, @RequestBody ParticipantRequestPayload payload){
        Optional<Participant> participant = this.repository.findById(id);

        if (participant.isPresent()){
            Participant rawParticipant = participant.get();
            rawParticipant.setIsConfirmed(true);
            rawParticipant.setName(payload.name());

            this.repository.save(rawParticipant);

            return ResponseEntity.ok(rawParticipant);
        }

        return ResponseEntity.notFound().build();
    }
}


Considerações Finais:
Este projeto foi uma excelente oportunidade para aprofundar meus conhecimentos em Java e no ecossistema Spring. Estou empolgado para continuar aprimorando essa aplicação e explorar novas funcionalidades no futuro.

Se você tiver interesse em saber mais sobre o projeto ou discutir ideias, sinta-se à vontade para entrar em contato!
