# angular-cheat-sheet

SERVICES!

WHAT IS IT?
An Angular 2 service is simply a javascript function, along with its associated properties and methods, that can be included (via dependency injection) into Angular 2 components.

INJECTION?

INJECTABLE SERVICES:
The @Injectable() decorator tells TypeScript to emit metadata about the service. The metadata specifies that Angular may need to inject other dependencies into this service.

Code Example:
@Injectable()
export class NameService {
}



NAMING CONVENTION:
The naming convention for service files is the service name in lowercase followed by .service. For a multi-word service name, use lower dash-case. For example, the filename for SpecialSuperHeroService is special-super-hero.service.ts.


