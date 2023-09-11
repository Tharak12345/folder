package details.com.example.detailsservice.demo.controller;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.PutMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import details.com.example.detailsservice.demo.Service.DetailsService;
import details.com.example.detailsservice.demo.entity.Details;

@RestController
@RequestMapping("/details")
public class DetailsController {
	@Autowired
	private DetailsService detailsService;
	@PostMapping("/")
	public ResponseEntity<Details> saveDetails(@RequestBody Details details) {
		return new ResponseEntity<Details>(detailsService.saveDetails(details),HttpStatus.CREATED);
	}
	@GetMapping("/fetch-all")
	public ResponseEntity<List<Details>> getAllDetails(){
		return new ResponseEntity<>(detailsService.getAllDetails(),HttpStatus.OK);
	}
	@GetMapping("/{id}")
	public ResponseEntity<Details> getByDetailsId(@PathVariable("id") long id){
		return new ResponseEntity<Details>(detailsService.getByDetailsId(id),HttpStatus.OK);
	}
	@PutMapping("/{id}")
	public ResponseEntity<Details> updateByDetailsId(@PathVariable("id") long id, @RequestBody Details details){
		return new ResponseEntity<Details>(detailsService.updateByDetailsId(id, details),HttpStatus.OK);
	}
	@DeleteMapping("/{id}")
	public ResponseEntity<Details> DeleteByDetailsId(@PathVariable("id") long id){
		return new ResponseEntity<Details>(detailsService.DeleteByDetailsId(id),HttpStatus.OK);
	}

}
